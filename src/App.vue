<template>

  <v-app id="inspire">
    <v-app-bar
      app
      color="#0b525b"
      flat
    >


      <v-tabs
        centered
        class="ml-n9"
        color="white"
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

    <v-main style="background-color: #212f45">
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
        {text: 'Karte',
        path: '/'},
        {text: 'O meni',
        path: '/Omeni'},
        {text: 'O predmetu',
        path: '/Opredmetu'},
      ],
    }),
};

</script>


