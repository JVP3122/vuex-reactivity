<template>
  <div>
    {{ tableTitles }}
    <v-card>
      <v-card-title>
        <p class="title ma-0">Table Visibility</p>
      </v-card-title>
      <v-divider class="mx-5"></v-divider>
      <v-card-text>
        <v-layout row wrap fill-height>
          <v-checkbox
            v-for="(title, idx) in tableTitles"
            v-model="displayTables"
            :label="title"
            :value="title"
            :key="idx"
            class="mx-1"
            multiple
          ></v-checkbox>
        </v-layout>
      </v-card-text>
      <v-card-actions>
        <v-switch
          v-model="showAll"
          :label="showAll ? 'Hide All' : 'Show All'"
        ></v-switch>
        <v-spacer></v-spacer>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
  import { mapState, mapGetters } from 'vuex'
  export default {
    name: "TableChoices",
    props: ['tableTitles'],
    data() {
      return {
        showAll: false,
        displayTables: [],
      }
    },
    methods: {
    },
    computed: {
      ...mapState({
        pageName: state => state.pageName,
      }),
      ...mapGetters({
        tableVisibility: 'getTableVisibility',
      }),
    },
    watch: {
      showAll(bool) {
        bool ?
          this.displayTables = this.tableTitles :
          this.displayTables = []
      },
      displayTables: {
        handler() {
          let tableObj = {};
          this.tableTitles.forEach(title => { tableObj[title] = this.displayTables.indexOf(title) > -1 })
          this.$store.commit('setTableVisibility', {page: this.pageName, tables: tableObj})
          if (this.displayTables.length === this.tableTitles.length) {
            this.showAll = true
          } else if (this.displayTables.length === 0) {
            this.showAll = false
          }
        }
      },
    }
  }
</script>

<style scoped>

</style>