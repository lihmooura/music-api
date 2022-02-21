<template>
  <v-app>
    <v-layout wrap>
      <v-flex class="d-flex justify-center align-center">
        <v-card width="700">
          <v-text-field outlined class="pa-3" label="Search" />
          <v-btn
            class="ma-3 d-flex align-right justify-right"
            @click="Search"
            :loading="loader"
            ><v-icon>mdi-magnify</v-icon></v-btn
          >
        </v-card>
      </v-flex>
      <v-flex wrap v-if="loader" xs12 class="d-flex align-center flex-column">
        <v-img src="" />
      </v-flex>
      <v-flex
        v-else
        lg2
        md3
        sm4
        xs6
        class="white"
        v-for="(item, index) in results"
        :key="index"
      >
      </v-flex>

      <v-flex
        v-if="results.length == 0 && loader == false"
        xs12
        class="d-flex align-center flex-column"
      >
        <v-img src="" />
      </v-flex>
    </v-layout>
  </v-app>
</template>

<script>
import axios from "axios";
export default {
  name: "Dashboard",
  data() {
    return {
      artist: "",
      results: [],
      loader: false,
    };
  },
  methods: {
    Search() {
      this.results = [];
      this.searchAPI();
    },
    searchAPI() {
      if (this.artist != "") {
        this.loader = true;
        axios
          .get(
            `https://itunes.apple.com/search?media=music&entity=song&term=${this.artist}`
          )
          .then((res) => {
            if (res.data.results) {
              res.data.results.forEach((element) => {
                this.results.push(element);
              });
              this.loader = false;
            }
            console.log(this.results);
          });
      }
    },
  },
  mounted() {
    this.searchAPI();
  },
};
</script>
