<script>
export default {
  name: "CardComp",
  props: {
    cardArray: Array,
  },
};
</script>
<template>
  <div class="card">
    <div class="img-card">
      <!-- ---- -->
    </div>
    <div class="text-card">
      <h3>{{ cardArray.title }}</h3>
      <p>{{ cardArray.original_title }}</p>
      <p>{{ cardArray.original_language }}</p>
      <p>{{ cardArray.vote_average }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  height: 500px;
  width: calc(100% / 5);
  background-color: #fff;
  padding: 20px;
  display: flex;
  align-items: flex-end;
  margin-bottom: 30px;
}

.text-card {
  padding: 5px;
  height: 35%;
  width: 100%;
  border: 1px solid black;
}
</style>
