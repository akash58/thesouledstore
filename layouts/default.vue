<template>
  <v-app>
    <v-toolbar flat fixed app color="#fff">
      <v-toolbar-side-icon class="hidden-sm-and-up" @click="drawer = !drawer"></v-toolbar-side-icon>
      <a href="/" class="pr">
        <img src="https://www.thesouledstore.com/static/img/newlogo.8dcc6cc.png" alt="logo" width="70" height="45">
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABcAAAAQCAYAAAD9L+QYAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6RkEwODk1MUZGNkNEMTFFNzg2QkRBQzUwNzZCN0Y0QUIiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6RkEwODk1MjBGNkNEMTFFNzg2QkRBQzUwNzZCN0Y0QUIiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDpGQTA4OTUxREY2Q0QxMUU3ODZCREFDNTA3NkI3RjRBQiIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDpGQTA4OTUxRUY2Q0QxMUU3ODZCREFDNTA3NkI3RjRBQiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PivGwz8AAAMfSURBVHjatFRfSFNRGP/O3d2c06lTkQQ1zX9LTUhqRUWpD4GlghVSFPlUEPVQBj2VkvOpp/ClejQhQlIxNMEH/wRSmLoyFJelLiMR55zb7ry7u/eezjnToS7qyQ/O/XfO9zu/7/f77kEYY9ir4FWHA1SPh1MWHKek7rf3lbm5Ak16xlzU9avPdaWlXWzVFgGEAIsigCQB6HSgzMwA9vpAfNkG+ps3OHl8QtVfuQzIZCJrATiSgLDgP++3NvcF+vurlaWlHGlo8Kzv7r22QGdnPWg0/yNoQTExXf4m6xReXW0BjksOM8eBQKpgbX6qLi8buMREAFUFSEgA7HbH+J+9uM2lpdk0mZmDeGMDkMEAKDqaVcAKiYsrERoaX8lfJrOBfJdtNrMq+NJirU3XSGV+Ljhhu6BMTR9A8fEh4E0ZKBBe/HlAGhiopYm7g7AFsbX1gTxjz6a59B0lJUHgTUeNNDJSzZgHh9+XA4dCbLabq9UC9vtBmf1erMwvpGOvd5GUDXhtDahUyGgslCc+FzPZ6KDENu9ST2+VrqzsNa/Oz+dSINjdNXQzngd1xWmSR0dTyUaLmBoZDLI5Ulme6vWaduRQDGa0vSCkuSjqiQmRNlFpyELwePjgp9Eo2BABEU9YJygKnY8mLPkt/cNBsIg/sQwc6fViWOtdzBnTOKOsPWIJUIlwcAfzDQIkR1RMsIjpPgbOZWXNgt1eBHr9Tmnos6wAl5Li4o9bfhPNgWnuCmv+jTMa10iX7dshJSGkMedPM3DtmdMD0ru+mggGhCHS8aDJyfmqycz6RUFRbh5hFSKBEhKm5InxSdluP8hkor7JMtmAA11lZQ9TSFtyuFNTWDCH19chrD2VhMiAyJ+qKy9vB9LjEZYIAujr6p7w5vwfeN3D3rFzFaJqL3XpTp7oZosUhwNJHz5WuY4eE1bS92OnuQA7MzLxatEhn9jeXk/PHkyqYIMwU30+UF0udg+OjYE0NGzx3rrT4a44Ny08traobncyyyGDp1cUY+g1PHpY8dezhZb87xjFfuGiobGBnS3bmwPt5anIwR7GHwEGAC5hnE6HKVfrAAAAAElFTkSuQmCC" alt="logo" width="15" class="sec-img">
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
        <a href="/" class="pr">
          <img src="https://www.thesouledstore.com/static/img/newlogo.8dcc6cc.png" alt="logo" width="50" height="35">
          <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABcAAAAQCAYAAAD9L+QYAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6RkEwODk1MUZGNkNEMTFFNzg2QkRBQzUwNzZCN0Y0QUIiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6RkEwODk1MjBGNkNEMTFFNzg2QkRBQzUwNzZCN0Y0QUIiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDpGQTA4OTUxREY2Q0QxMUU3ODZCREFDNTA3NkI3RjRBQiIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDpGQTA4OTUxRUY2Q0QxMUU3ODZCREFDNTA3NkI3RjRBQiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PivGwz8AAAMfSURBVHjatFRfSFNRGP/O3d2c06lTkQQ1zX9LTUhqRUWpD4GlghVSFPlUEPVQBj2VkvOpp/ClejQhQlIxNMEH/wRSmLoyFJelLiMR55zb7ry7u/eezjnToS7qyQ/O/XfO9zu/7/f77kEYY9ir4FWHA1SPh1MWHKek7rf3lbm5Ak16xlzU9avPdaWlXWzVFgGEAIsigCQB6HSgzMwA9vpAfNkG+ps3OHl8QtVfuQzIZCJrATiSgLDgP++3NvcF+vurlaWlHGlo8Kzv7r22QGdnPWg0/yNoQTExXf4m6xReXW0BjksOM8eBQKpgbX6qLi8buMREAFUFSEgA7HbH+J+9uM2lpdk0mZmDeGMDkMEAKDqaVcAKiYsrERoaX8lfJrOBfJdtNrMq+NJirU3XSGV+Ljhhu6BMTR9A8fEh4E0ZKBBe/HlAGhiopYm7g7AFsbX1gTxjz6a59B0lJUHgTUeNNDJSzZgHh9+XA4dCbLabq9UC9vtBmf1erMwvpGOvd5GUDXhtDahUyGgslCc+FzPZ6KDENu9ST2+VrqzsNa/Oz+dSINjdNXQzngd1xWmSR0dTyUaLmBoZDLI5Ulme6vWaduRQDGa0vSCkuSjqiQmRNlFpyELwePjgp9Eo2BABEU9YJygKnY8mLPkt/cNBsIg/sQwc6fViWOtdzBnTOKOsPWIJUIlwcAfzDQIkR1RMsIjpPgbOZWXNgt1eBHr9Tmnos6wAl5Li4o9bfhPNgWnuCmv+jTMa10iX7dshJSGkMedPM3DtmdMD0ru+mggGhCHS8aDJyfmqycz6RUFRbh5hFSKBEhKm5InxSdluP8hkor7JMtmAA11lZQ9TSFtyuFNTWDCH19chrD2VhMiAyJ+qKy9vB9LjEZYIAujr6p7w5vwfeN3D3rFzFaJqL3XpTp7oZosUhwNJHz5WuY4eE1bS92OnuQA7MzLxatEhn9jeXk/PHkyqYIMwU30+UF0udg+OjYE0NGzx3rrT4a44Ny08traobncyyyGDp1cUY+g1PHpY8dezhZb87xjFfuGiobGBnS3bmwPt5anIwR7GHwEGAC5hnE6HKVfrAAAAAElFTkSuQmCC" alt="logo" width="10" class="sec-img-nav">
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
        <v-list-tile
          @click=""
        >
          Login
        </v-list-tile>
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
        drawer: false,
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
  .pr {
    position: relative;
  }
  .sec-img {
    position: absolute;
    top: 23%;
    right: 46px;
  }
  .sec-img-nav {
    position: absolute;
    top: 23%;
    right: 33px;
  }
</style>
