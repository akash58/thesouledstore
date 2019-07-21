<template>
  <v-app>
    <v-toolbar flat fixed app color="#fff">
      <a href="/">
        <img src="https://www.thesouledstore.com/static/img/newlogo.8dcc6cc.png" alt="logo" width="70" height="45">
      </a>
      <v-btn
        color="white"
        class="elevation-0"
      >
        SHOP
        <v-icon center size="20">keyboard_arrow_down</v-icon>
      </v-btn>
      <v-btn
        color="white"
        class="elevation-0"
      >
        OFFICIAL MARCH
        <v-icon center size="20">keyboard_arrow_down</v-icon>
      </v-btn>
      <v-spacer></v-spacer>
      <v-btn flat icon><v-icon size="24" class="px-2 hidden-sm-and-down">search</v-icon></v-btn>
      <v-btn flat icon><v-icon size="24" class="px-2 hidden-sm-and-down">person_outline</v-icon></v-btn>
      <v-btn flat icon><v-icon size="24" class="px-2 hidden-sm-and-down">local_grocery_store</v-icon></v-btn>
    </v-toolbar>
    <nuxt />
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        fixed: false,
        title: 'Vuetify.js'
      }
    }
  }
</script>
