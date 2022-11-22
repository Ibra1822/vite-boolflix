<script>
export default {
  name: "CardComp",
  props: {
    cardArray: Array,
  },
  data() {
    return {};
    // vote_average
  },
  methods: {},
  mounted() {},
};
</script>
<template>
  <div class="card">
    <div class="img-card">
      <img
        :src="'https://image.tmdb.org/t/p/w342/' + cardArray.poster_path"
        :alt="cardArray.title || cardArray.name"
      />
    </div>
    <div class="text-card">
      <h3>{{ cardArray.title || cardArray.name }}</h3>
      <p>{{ cardArray.original_title || cardArray.original_name }}</p>
      <i :class="cardArray.flag"></i>
      <p>{{ cardArray.vote_average }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  height: 500px;
  width: calc(100% / 5);
  min-width: 250px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  margin-bottom: 30px;
  margin: auto;
}
.img-card {
  height: 65%;
  width: 100%;
  border: 1px solid black;
  cursor: pointer;
  img {
    height: 100%;
    width: 100%;
    object-fit: cover;
  }
}

.text-card {
  padding: 5px;
  height: 35%;
  width: 100%;
  color: #fff;
  border: 0px 1px 1px solid black;
  cursor: pointer;
  h3 {
    font-size: 1.2rem;
  }
}
</style>
