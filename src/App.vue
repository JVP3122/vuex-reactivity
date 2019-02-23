<template>
  <v-app>
    <v-content>
      <v-container fluid>
        <v-layout>
          <v-flex shrink>
            <Page />
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Page from './components/Page'

export default {
  name: 'App',
  components: {
    Page
  },
  data () {
    return {
      //
    }
  }
}
</script>
