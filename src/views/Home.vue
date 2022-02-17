<template>
  <div style="background-color: #212f45">
    <v-container>
      <v-row >
        <v-col>
          <v-dialog
      v-model="adddialog"
      width="500"
    >
      <template v-slot:activator="{ on, attrs }"><center>
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Dodaj
        </v-btn></center>
      </template>

      <v-card>
        <v-card-title class="text-h5 grey lighten-2">
          Dodaj novu kartu
        </v-card-title>

        <v-card-text>
          <nova-forma></nova-forma>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            text
            @click="adddialog = false; alertt = true"
          >
            Dodaj
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
        </v-col>
      </v-row>




      <v-row style="justify-content: center">
        <v-col cols="4">
        <v-text-field
        v-model="search"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
      </v-col>
      <v-col cols="4" sm="4">
      <v-btn
      depressed
      color="blue" 
      @click="dohvatiime()">Pretraži</v-btn>
      <v-btn
      depressed
      color="grey" 
      @click="dohvatiPodatke()">Sve karte</v-btn>
        </v-col>
      </v-row>
              <v-row style="justify-content: center"> 
                <v-col cols="8" style="justify-content: center">
          <v-autocomplete
            v-model="pretraga"
            :items="items"


            multiple
            solo
            @input="ponudeno(pretraga)"
          ></v-autocomplete>
        </v-col>
            </v-row>
            <v-row>
                      <v-col>
              <v-alert
              v-model="alertt"
      dense
      text
      type="success"
    >
      Uspješno ste dodali kartu!
    </v-alert>
        </v-col>
            </v-row>
      <v-row>
        <v-col cols="12" sm="4" v-for="karta in karte" :key="karta" >

          <karta :karta="karta"></karta>

        </v-col>
      </v-row>
                <v-row style="justify-content: center">
        <v-pagination
        v-model="page"
        total-visible="10"
        :length="Math.ceil(ukupno/6)"
        @click="page + 1"
        >Filter po energiji</v-pagination>
      </v-row>

    </v-container>

  </div>
</template>


<script>
import Karta from '../components/Karta.vue';
import NovaForma from '../components/NovaForma.vue';
  export default {
  components: { Karta, NovaForma },
      name: 'Home',
  data: () => ({
      karte: [],
      page: 1,
      ukupno:0,
      search: '',
      name: '',
      pagesize: 6,
      items: ['Psychic', 'Lightning', 'Grass', 'Water', 'Fire', 'Metal', 'Darkness', 'Fighting'],
      pretraga: "",
      pagesize2: 12,
      adddialog: false,
      alertt: false,
    }),
        created() {
      this.dohvatiPodatke();
    },
      methods: {
    dohvatiPodatke: function () {
      let api = "https://api.pokemontcg.io/v2/cards?pageSize=6" 
      this.axios.get(api, {params: {
        'page': this.page,
      }}).then((response) => {
        console.log(response.data.data)
        this.karte = response.data.data;
        this.ukupno = response.data.totalCount
      });
    },
        dohvatiime: function () {
      let api = "https://api.pokemontcg.io/v2/cards?q=name:" + this.search
      this.axios.get(api).then((response) => {
        
        console.log(response.data.data)
        this.karte = response.data.data;
      });
    },
      ponudeno: function (types) {
      let api = "https://api.pokemontcg.io/v2/cards?q=types:" + types
      this.axios.get(api, { params: {
                'page': this.page,
                'pageSize': this.pagesize2

      }}).then((response) => {
                
        console.log(response.data.data)
        this.karte = response.data.data;
      });
    },
  },
    watch: {
      page: function() {
        this.dohvatiPodatke();
      }
    }
  }

</script>

