<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>Vue.js Electron</v-toolbar-title>
    </v-app-bar>
    
    <v-main>
      <home></home>
    </v-main>

  </v-app>
</template>

<script>
import Home from './components/Home.vue';

export default {
  name: 'App',

  components: {
    Home
  },

  data: () => ({
    //
  }),
};
</script>
