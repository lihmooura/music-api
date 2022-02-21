<template>
  <v-app>
    <v-layout wrap>
      <v-flex xs12 class="d-flex justify-center">
        <v-card width="650" height="100px" class="d-flex mt-6">
          <v-text-field
            outlined
            class="pa-3 field"
            label="Search"
            v-model="artist"
          />
          <v-btn
            icon
            class="mt-6 mr-3 d-flex align-right justify-right"
            @click="HandleOnClick"
            :loading="loader"
            ><v-icon>mdi-magnify</v-icon></v-btn
          >
        </v-card>
      </v-flex>
      <v-flex lg3 class="pa-4" v-for="(item, index) in results" :key="index">
        <CardInfo :info="item" />
      </v-flex>

      <v-flex
        v-if="results.length == 0 && loader == false"
        xs12
        class="d-flex align-center flex-column"
      >
        <v-img
          src="https://assets10.lottiefiles.com/packages/lf20_n2m0isqh.json"
        />
      </v-flex>
    </v-layout>
  </v-app>
</template>

<script>
import axios from "axios";
import CardInfo from "../components/CardInfo.vue";
export default {
  name: "Dashboard",
  components: {
    CardInfo,
  },
  data() {
    return {
      artist: "",
      results: [],
      loader: false,
    };
  },
  methods: {
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
    HandleOnClick() {
      this.results = [];
      this.searchAPI();
    },
  },
  mounted() {
    this.searchAPI();
  },
};
</script>
