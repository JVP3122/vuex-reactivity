<template>
  <div>
    tableVisibility {{ tableVisibility }}
  </div>
</template>

<script>
  import Dog from '@/components/Dog'
  import Cat from '@/components/Cat'
  import Bird from '@/components/Bird'
  import { mapState, mapGetters } from 'vuex'
  export default {
    name: "LandingPage",
    components: {
      Dog,
      Cat,
      Bird,
    },
    data() {
      return {
        items: {},
        headers: {},
      }
    },
    computed: {
      ...mapState({
        pageName: state => state.pageName,
      }),
      ...mapGetters({
        tableVisibility: 'getTableVisibility'
      })
    },
    watch: {
      tableVisibility: {
        handler() { console.log('tableVisibility in LandingPage.vue', this.tableVisibility)},
        deep: true
      },
    }
  }
</script>

<style scoped>

</style>