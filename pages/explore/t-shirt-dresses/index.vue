<template>
  <div class="white">
    <div class="mt-5 pt-3">
      <img src="https://images.thesouledstore.com/public/theSoul/uploads/catalog/category/catban-020190701122615.jpg" width="100%">
    </div>
    <v-container fluid grid-list-xl class="py-0">
      <v-layout row wrap justify-space-around>
        <v-flex xs12 sm3 class="mt-3">
          <v-expansion-panel popout>
            <v-expansion-panel-content
              v-for="(item,i) in expansions"
              :key="i"
            >
              <template v-slot:header>
                <div>{{item.text}}</div>
              </template>
              <v-card class="mx-2 scroll-y" max-height="210">
                <v-text-field
                  label="Search"
                  solo
                ></v-text-field>
                <v-checkbox-group v-model="ex7" column >
                  <v-checkbox
                    label="Game Of Thrones"
                    color="success"
                    value="red"
                    class="my-0"
                  ></v-checkbox>
                  <v-checkbox
                    label="Start Wars"
                    color="success"
                    value="red darken-3"
                    class="my-0"
                  ></v-checkbox>
                  <v-checkbox
                    label="Marvel"
                    color="success"
                    value="indigo"
                    class="my-0"
                  ></v-checkbox>
                  <v-checkbox
                    label="Souled Store"
                    color="success"
                    value="indigo darken-3"
                    class="my-0"
                  ></v-checkbox>
                  <v-checkbox
                    label="WWE"
                    color="success"
                    value="orange"
                    class="my-0"
                  ></v-checkbox>
                  <v-checkbox
                    label="Harry Potter"
                    color="success"
                    value="orange darken-3"
                    class="my-0"
                  ></v-checkbox>
                </v-checkbox-group>
              </v-card>
            </v-expansion-panel-content>
          </v-expansion-panel>
          <v-layout justify-center>
            <v-btn outline color="#1DE9B6">Apply</v-btn>
            <v-btn outline color="#1DE9B6">Clear</v-btn>
          </v-layout>
        </v-flex>
        <v-flex xs12 sm9>
          <v-breadcrumbs :items="items" divider="/" class="py-2"></v-breadcrumbs>
          <v-divider></v-divider>
          <v-layout row wrap>
            <v-flex v-for="(n, ind) in 6" :key="ind">
              <v-card class="elevation-0 hc">
                <div class="img-holder">
                  <img src="https://images.thesouledstore.com/public/theSoul/uploads/catalog/product/20190614101030-1.jpg?h=282&w=282" width="273" class="prod1">
                  <img src="https://images.thesouledstore.com/public/theSoul/uploads/catalog/product/20190614101042-1.jpg?h=282&w=282" width="273" class="prod2">
                </div>
                <div class="mx-2">
                  <div class="pa-1">
                    Batman: Classic Logo
                  </div>
                  <v-divider></v-divider>
                  <v-layout align-center justify-space-between wrap class="ma-1">
                    <div class="text-xs-right">Joggers</div>
                    <div class="text-xs-left">Rs.899</div>
                  </v-layout>
                  <v-layout align-center justify-space-between wrap class="ma-1 light-blue--text">
                    <div class="text-xs-right">
                      For Excl. Member
                      <v-icon size="16" class="light-blue--text">info</v-icon>
                    </div>
                    <div class="text-xs-left">Rs.799</div>
                  </v-layout>
                </div>
              </v-card>
            </v-flex>
          </v-layout>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
  export default {
    data: () => ({
      items: [
        {
          text: 'Home',
          disabled: false,
          href: '/'
        },
        {
          text: 'Joggers',
          disabled: true,
          href: '/explore/joggers'
        }
      ],
      expansions: [
        {
          text: 'THEMES'
        },
        {
          text: 'GENERS'
        },
        {
          text: 'SORT'
        }
      ],
      ex7: 'red'
    })
  }
</script>

<style scoped>
  .prod2{display:none;}
  .img-holder:hover .prod2{display:block;}
  .img-holder:hover .prod1{display:none;}
  .hc {
    cursor: pointer;
  }
</style>