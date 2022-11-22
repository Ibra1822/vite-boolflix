<script>
import CardComp from "./CardComp.vue";
import { store } from "../Data/store";
export default {
  name: "MainComp",
  components: {
    CardComp,
  },
  data() {
    return {
      store,
    };
  },
  methods: {},
};
</script>
<template>
  <h2>Film trovati {{ store.movieArray.length }}</h2>
  <div class="container-card">
    <CardComp
      v-for="item in store.movieArray"
      :key="item.id"
      :cardArray="item"
    />
  </div>
  <h2>Serie Tv trovate {{ store.tvArray.length }}</h2>
  <div class="container-card">
    <CardComp v-for="item in store.tvArray" :key="item.id" :cardArray="item" />
  </div>
</template>

<style lang="scss" scoped>
h2 {
  font-size: 1.8rem;
  color: #de1a28;
  text-align: center;
  text-transform: uppercase;
  margin-bottom: 25px;
}
.container-card {
  width: 90%;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
}
</style>
