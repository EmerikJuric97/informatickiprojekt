<template>
  <div style="padding: 20px">
    <v-container>
      <v-row>
        <v-col cols="4">
          <v-card class="mx-auto" max-width="344" outlined>
            <v-list-item three-line>
              <v-list-item-content>
                <div class="text-overline mb-4">
                  test
                </div>
                <v-list-item-title class="text-h5 mb-1">
                  test
                </v-list-item-title>
                <v-list-item-subtitle>
                  test
                </v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-avatar
                tile
                size="80"
                color="grey"
              ></v-list-item-avatar>
            </v-list-item>

            <v-card-actions>
              <v-btn color="primary" outlined rounded text> Button </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
      <v-row>
        <v-pagination
        v-model="page"
        :length="6"
        ></v-pagination>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { config } from 'vue/types/umd';

export default {
  name: 'Home',

  data: () => ({
      karte: [],
      page:[]
    }),
    created() {
      this.dohvatiPodatke();
    },
      methods: {
    dohvatiPodatke: function () {
      let api = "https://pokemon-tcg-card-prices.p.rapidapi.com/card/c4cbb4b6-ceba-4b14-8e28-ad2b590ccd59"
      this.axios.get(api, {
        params:{
          'x-rapidapi-host': 'pokemon-tcg-card-prices.p.rapidapi.com',
          'x-rapidapi-key': '71a8e7b6a9mshcb1fdc534b8cd28p1f7c40jsn453692f98fa9'
        }
      }).then((response) => {
        this.karte = response.data;
      });
    },
  },
};
</script>

