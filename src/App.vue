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
    getApi(type) {
      axios
        .get(store.movieApi + type, {
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
      this.getApi("tv");
      this.getApi("movie");
    },
  },
  mounted() {
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
