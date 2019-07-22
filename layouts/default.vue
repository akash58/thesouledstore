<template>
  <v-app>
    <v-toolbar flat fixed app color="#fff">
      <v-toolbar-side-icon class="hidden-sm-and-up" @click="drawer = !drawer"></v-toolbar-side-icon>
      <a href="/">
        <img src="https://www.thesouledstore.com/static/img/newlogo.8dcc6cc.png" alt="logo" width="70" height="45">
      </a>
      <v-menu open-on-hover bottom offset-y>
        <template v-slot:activator="{ on }">
          <v-btn
            color="white"
            class="elevation-0 header-new"
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
            class="elevation-0 header-new"
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
      <v-btn flat icon class="header-new"><v-icon size="24" class="px-2 hidden-sm-and-down">search</v-icon></v-btn>
      <v-btn flat icon class="header-new"><v-icon size="24" class="px-2 hidden-sm-and-down">person_outline</v-icon></v-btn>
      <v-btn flat icon class="header-new"><v-icon size="24" class="px-2 hidden-sm-and-down">local_grocery_store</v-icon></v-btn>
    </v-toolbar>
    <v-navigation-drawer
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
    >
      <v-toolbar flat  class="text-xs-center justify-center">
        <a href="/">
          <img src="https://www.thesouledstore.com/static/img/newlogo.8dcc6cc.png" alt="logo" width="50" height="35">
        </a>
      </v-toolbar>
      <v-list>
        <v-list-group
          v-for="item in items"
          :key="item.title"
          v-model="item.active"
          :prepend-icon="item.action"
          no-action
        >
          <template v-slot:activator>
            <v-list-tile>
              <v-list-tile-content>
                <v-list-tile-title>{{ item.title }}</v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>
          </template>

          <v-list-tile
            v-for="subItem in item.items"
            :key="subItem.title"
            @click=""
          >
            <v-list-tile-content>
              <v-list-tile-title>{{ subItem.title }}</v-list-tile-title>
            </v-list-tile-content>

            <v-list-tile-action>
              <v-icon>{{ subItem.action }}</v-icon>
            </v-list-tile-action>
          </v-list-tile>
        </v-list-group>
        </v-list>
    </v-navigation-drawer>
    <nuxt />
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        clipped: false,
        drawer: true,
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
        ],
        items: [
          {
            action: 'local_activity',
            title: 'Shop',
            items: [
              { title: 'Joggers' }
            ]
          },
          {
            action: 'home',
            title: 'Official March',
            active: true,
            items: [
              { title: 'tshirt' },
              { title: 'Captain American' },
              { title: 'harry-Potter' }
            ]
          }
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
