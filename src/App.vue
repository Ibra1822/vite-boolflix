<script>
import HeaderComp from "./components/HeaderComp.vue";
import MainComp from "./components/MainComp.vue";
import { store } from "./Data/store";
import axios from "axios";

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    getApi(type, isPopular = false) {
      let api;
      if (isPopular) api = "https://api.themoviedb.org/3/movie/popular/";
      else api = store.movieApi + type;
      store.isLoaded = false;
      axios
        .get(api, {
          params: {
            query: store.paramToSearch,
            api_key: store.api_key,
            language: store.language,
          },
        })

        .then((result) => {
          console.log(result.data.results);
          if (type === "movie") {
            store.movieArray = result.data.results;
          } else {
            store.tvArray = result.data.results;
          }
          store.isLoaded = true;
          store.movieArray.forEach((item) => {
            item.flag = "fi fi-" + item.original_language;
            if (item.original_language == "en") {
              item.flag = "fi fi-gb";
            } else if (item.original_language == "ja") {
              item.flag = "fi fi-jp";
            }
          });
          store.tvArray.forEach((item) => {
            item.flag = "fi fi-" + item.original_language;
            if (item.original_language == "en") {
              item.flag = "fi fi-gb";
            } else if (item.original_language == "ja") {
              item.flag = "fi fi-jp";
            }
          });
        })
        .catch((error) => {
          console.log(error);
        });
    },
    find() {
      this.getApi("movie", true);
      store.tvArray = [];
      store.movieArray = [];
      if (store.gender === "") {
        this.getApi("movie");
        this.getApi("tv");
      } else {
        this.getApi(store.gender);
      }
    },
  },

  mounted() {
    this.getApi("movie", true);
    this.find();
  },
};
</script>
<template>
  <HeaderComp @startSearch="find" />
  <MainComp />
</template>

<style lang="scss">
@use "./styles/general.scss";
</style>
