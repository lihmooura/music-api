<template>
  <v-card height="290px" class="card-info">
    <v-card-title class="font-weight-light">
      {{ info.artistName }}
    </v-card-title>
    <v-card-subtitle class="font-weight-normal">
      {{ info.trackName }}
    </v-card-subtitle>

    <v-img class="ma-4" :src="info.artworkUrl100" height="130px" />

    <v-btn @click="onFavClick(info)" icon>
      <v-icon color="grey" v-if="!isFavorite">mdi-heart-outline</v-icon>
      <v-icon color="red" v-if="isFavorite">mdi-heart</v-icon>
    </v-btn>
  </v-card>
</template>

<script>
export default {
  props: ["info"],
  data() {
    return {
      isFavorite: false,
    };
  },
  methods: {
    onFavClick() {
      this.isFavorite = true;
    },
  },
};
</script>

<style>
.card-info {
  border-radius: 10px;
  border-color: black;
  background: grey lighten-5;
  cursor: pointer;
}
.card-info:hover {
  -webkit-box-shadow: 5px 5px 29px 6px rgba(123, 123, 123, 0.85);
  box-shadow: 5px 5px 29px 6px rgba(123, 123, 123, 0.214);
}
</style>

