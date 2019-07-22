<template>
  <v-app>
    <v-toolbar flat fixed app color="#fff">
      <a href="/">
        <img src="https://www.thesouledstore.com/static/img/newlogo.8dcc6cc.png" alt="logo" width="70" height="45">
      </a>
      <v-menu open-on-hover bottom offset-y>
        <template v-slot:activator="{ on }">
          <v-btn
            color="white"
            class="elevation-0"
            v-on="on"
          >
            SHOP
            <v-icon center size="20">keyboard_arrow_down</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-tile
            v-for="(item, index) in list1"
            :key="index"
            @click=""
          >
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile>
        </v-list>
      </v-menu>
      <v-menu open-on-hover bottom offset-y>
        <template v-slot:activator="{ on }">
          <v-btn
            color="white"
            class="elevation-0"
            v-on="on"
          >
            OFFICIAL MARCH
            <v-icon center size="20">keyboard_arrow_down</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-tile
            v-for="(item, index) in list1"
            :key="index"
            @click=""
          >
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile>
        </v-list>
      </v-menu>
      <div class="font-weight-medium subheading header-new hidden-sm-and-down">
        Joggers
      </div>
      <span class="red--text caption font-weight-bold mb-2 pl-1 hidden-sm-and-down">New</span>
      <div class="font-weight-medium subheading pl-4 header-new hidden-sm-and-down">
        Exclusive
      </div>
      <span class="red--text caption font-weight-bold mb-2 pl-1 hidden-sm-and-down">New</span>
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
        list1: [
          { title: 'T-Shirts' },
          { title: 'Joggers' },
          { title: 'Track Pants' },
          { title: 'Shirts' }
        ],
        list2: [
          { title: 'Game Of Thrones' },
          { title: 'Star Wars' },
          { title: 'Harry Potter' },
          { title: 'Angry Birds' }
        ]
      }
    }
  }
</script>

<style scoped>
  .header-new:hover {
    color: red;
    cursor: pointer;
  }
</style>
