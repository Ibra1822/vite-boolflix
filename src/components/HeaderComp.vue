<script>
import { store } from "../Data/store";

export default {
  name: "HeaderComp",
  data() {
    return {
      store,
    };
  },
};
</script>
<template>
  <header>
    <div class="cont-logo">
      <img src="../assets/img/logo-boolflix.png" alt="" />
    </div>
    <div class="find">
      <input
        v-model="store.paramToSearch"
        type="text"
        name=""
        id=""
        placeholder="Cerca un film"
      />
      <button @click="$emit('startSearch')">Search</button>
    </div>
  </header>
</template>

<style lang="scss" scoped>
header {
  height: 150px;
  background-color: black;
  display: flex;
  align-items: center;
  justify-content: space-between;
  .cont-logo {
    width: 150px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 15px;
    img {
      width: 100%;
      cursor: pointer;
    }
  }
  input,
  button {
    padding: 10px 15px;
    margin-right: 15px;
  }
}
</style>
