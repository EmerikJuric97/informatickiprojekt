<template>

  <v-app id="inspire">
    <v-app-bar
      app
      color="white"
      flat
    >


      <v-tabs
        centered
        class="ml-n9"
        color="grey darken-1"
      >
        <v-tab
          v-for="link in links"
          :key="link"
          :to="link.path"
        >
          {{ link.text }}
        </v-tab>
      </v-tabs>


    </v-app-bar>

    <v-main class="blue lighten-3">
      <v-container>
        <v-row>

          <v-col
            cols="12"
            sm="15"
          >
            <v-sheet
              min-height="70vh"
              rounded="lg"
            >
              <router-view></router-view>
            </v-sheet>
          </v-col>

        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>



<script>

export default {
  name: 'App',

  data: () => ({
      links: [
        {text: 'Naslovnica',
        path: '/'},
        {text: 'O meni',
        path: '/Omeni'},
        {text: 'O predmetu',
        path: '/Opredmetu'},
      ],
    }),
};

</script>


