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
</template>

<style lang="scss" scoped>
h2 {
  font-size: 1.8rem;
  color: #de1a28;
  text-align: center;
  text-transform: uppercase;
}
.container-card {
  width: 90%;
  background-color: #434343;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
}
</style>
