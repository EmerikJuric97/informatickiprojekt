<template>
<v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col
          cols="12"
        >
          <v-text-field
            v-model="ime"
            :rules="nameRules"
            :counter="10"
            label="Ime karte"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
        >
          <v-text-field
            v-model="set"
            :rules="nameRules"
            :counter="10"
            label="Set"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
        >
          <v-text-field
            v-model="broj"
            :rules="emailRules"
            type="number"
            label="Broj karte"
            required
          ></v-text-field>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
  export default {
    data () {
      return{
        ime: '',
        set: '',
        broj: '',
      }
    }
  }
</script>
