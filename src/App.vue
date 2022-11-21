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
    getApi() {
      axios
        .get(store.movieApi + "query=" + store.paramToSearch)
        .then((result) => {
          console.log(result.data.results);
          store.movieArray = result.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    find() {
      this.getApi();
      store.paramToSearch = "";
    },
  },
  mounted() {
    this.getApi();
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
