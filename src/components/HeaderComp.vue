<script>
import { store } from "../Data/store";

export default {
  name: "HeaderComp",
  props: {},
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
        placeholder="Cerca un Film o Serie Tv"
        @keyup.enter="$emit('startSearch')"
      />

      <select
        @change="$emit('startSearch')"
        v-model="store.gender"
        name=""
        id=""
      >
        <option selected value="">All</option>
        <option value="movie">Movie</option>
        <option value="tv">Tv</option>
      </select>

      <select
        v-if="store.paramToSearch !== ''"
        @change="$emit('startSearch')"
        v-model="store.language"
        name=""
        id=""
      >
        <option selected value="it-IT">Seleziona la lingua</option>
        <option value="en-GB">English</option>
        <option value="ru-RU">Russian</option>
        <option value="ar-SA">Arabic</option>
      </select>
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
  margin-bottom: 40px;
  .cont-logo {
    width: 150px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 45px;

    img {
      width: 200px;
      cursor: pointer;
    }
  }
  button,
  input,
  select {
    padding: 10px 15px;
    margin-right: 15px;
    background-color: transparent;
    color: #fff;
    border: 3px solid #de1a28;
    border-radius: 10px;
    font-size: 0.9rem;
  }
  input:focus-visible {
    outline: 2px solid #de1a28;
    border-radius: 10px;
  }
}
</style>
