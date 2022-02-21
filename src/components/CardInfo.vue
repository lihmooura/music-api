<template>
  <v-app>
    <v-layout>
      <v-flex>
        <v-card>
          <v-card-title>
            <v-img :src="info.artworkUrl100" height="130px" />
            <br />
            <p>{{ info.artistName }}</p>
          </v-card-title>
          <v-btn @click="onFavClick(info)" icon>
            <v-icon color="grey" v-if="!isFavorite">mdi-heart-outline</v-icon>
            <v-icon color="yellow" v-if="isFavorite">mdi-heart</v-icon>
          </v-btn>
        </v-card>
      </v-flex>
    </v-layout>
  </v-app>
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