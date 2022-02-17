<template>
  <v-app id="inspire">
    <v-main>
      <v-container>
        <v-row>
          <v-col
            v-for="karta in karte"
            :key="karta"
            cols="12"
            md="3"
            style="background-color: #023047"
          >
            <v-card height="200">
              {{ karta.name }}
              <img :src="karta.images.small" height="80px" width="40px">
              
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
              <v-pagination
      v-model="page"
      :length="4"
      circle
    ></v-pagination>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
  data: () => ({
      karte: [],
      page: 1,
    }),
        created() {
      this.dohvatiPodatke();
    },
      methods: {
    dohvatiPodatke: function () {
      let api = "https://api.pokemontcg.io/v2/cards/"
      this.axios.get(api).then((response) => {
        console.log(response.data.data)
        this.karte = response.data.data;
      });
    },
  },
};
</script>
