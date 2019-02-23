<template>
  <div>
    Page
    pageTitles {{ pageTitles }}
    <TableChoices :table-titles="tableTitles"/>
    <v-btn v-for="page in pageTitles" @click="setPageName(page)">Set page name {{ page }}</v-btn>
    <LandingPage/>
  </div>
</template>

<script>
  import { mapState, mapGetters } from 'vuex'
  import TableChoices from "./TableChoices";
  import LandingPage from "./LandingPage";
  export default {
    name: "Page",
    components: {LandingPage, TableChoices},
    computed: {
      ...mapState({
        pageName: state => state.pageName
      }),
      ...mapGetters([
        'tableTitles',
        'pageTitles',
      ])
    },
    methods: {
      setPageName(page) {
        this.$store.commit('setPageName', page)
      }
    }
  }
</script>

<style scoped>

</style>