<template>
  <div style="background-color: #212f45; justify-content: center">
    <v-container>
      <v-row style="justify-content: center">
        <v-col cols="4" style="justify-content: center">
      <h2 style="color:white; justify-content: center">Ime i prezime: Emerik Jurić</h2>
      </v-col>
      <v-row>
      <v-col>
      <h3 style="color:white">Završio sam Strojarsku tehničku školu u Osijeku te trenutno studiram studij Informatike u Orašju. Slobodno vrijeme volim
        provoditi s obitelji i prijateljima te se također bavim kao freelancer u području 3D modeliranja i animacije.
      </h3>
      </v-col>
      </v-row>
      </v-row>
    </v-container>
  </div>
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
