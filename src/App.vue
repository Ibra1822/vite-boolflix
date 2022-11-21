<script>
import HeaderComp from "./components/HeaderComp.vue";
import MainComp from "./components/MainComp.vue";
import axios from "axios";
import { store } from "./Data/store";

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
};
</script>
<template>
  <HeaderComp />
  <MainComp />
</template>

<style lang="scss">
@use "./styles/general.scss";
</style>
