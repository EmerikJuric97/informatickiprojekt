<template>
  <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="374"
    style="background-color: #212f45"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      height="510"
      :src="karta.images.small"
    ></v-img>

    <v-card-title style="justify-content: center; color: white">{{ karta.name }}</v-card-title>

    <v-card-text style="justify-content: center; color: grey">
      <div style="color: grey">{{ karta.flavorText }}</div>
      <div style="justify-content: center; color: lightgrey">Set: {{ karta.set.name }}</div>
      <div style="justify-content: center; color: lightgrey">Broj karte u setu: {{ karta.number }}</div>
    </v-card-text>


    <v-divider class="mx-4"></v-divider>




  </v-card>
</template>

<script>
  export default {
    props: ['karta']}
</script>
