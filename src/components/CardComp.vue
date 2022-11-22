<script>
export default {
  name: "CardComp",
  props: {
    cardArray: Array,
  },
  data() {
    return {};
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
      <div class="flag-cont">
        <i :class="cardArray.flag"></i>
      </div>
      <div class="cont-stars">
        <i
          v-for="(item, index) in 5"
          :key="index"
          class="fa-star"
          :class="index < Math.ceil(cardArray.vote_average / 2) ? 'fas' : 'far'"
        ></i>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  height: 430px;
  width: calc(100% / 5 - 50px);
  min-width: 240px;
  display: flex;
  align-items: flex-end;
  margin: auto;
  position: relative;
  margin-bottom: 35px;
  box-shadow: 0px 0px 25px #000;

  &:hover .text-card {
    height: 30%;
  }
  &:hover .img-card {
    opacity: 0.5;
  }
}
.img-card {
  height: 100%;
  width: 100%;
  border: 1px solid black;
  cursor: pointer;
  transition: all 0.6s;

  img {
    height: 100%;
    width: 100%;
    object-fit: cover;
    filter: grayscale(40%);
  }
}

.text-card {
  background-color: #000;
  color: #fff;
  cursor: pointer;
  position: absolute;
  transform: translate(-50% -50%);
  text-align: center;
  width: 100%;
  overflow-y: hidden;
  box-shadow: 0px 0px 35px #000;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 0;
  transition: 0.6s;
  h3 {
    font-size: 1.1rem;
    text-shadow: 0px 0px 2px #fff;
  }
  p {
    font-size: 0.8rem;
    margin-bottom: 8px;
    text-decoration: underline;
  }
  i {
    font-size: 0.8rem;
    text-shadow: 0px 0px 5px #fff;
    margin: 5px 0;
  }
}
</style>
