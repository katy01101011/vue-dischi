<template>
  <div class="d-flex flex-column justify-content-center align-items-center">
    <img src="../assets/logo-small.svg" alt="">
    <h1>Loading</h1>
  </div>
</template>

<script>
export default {
  name: "AppLoading",
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

div {
  width: 100%;
  height: calc(100vh - $header-height);

  img {
    width: 20rem;
    position: relative;
    bottom: 10rem;
  }

  h1 {
  color: white;
  font-size: 5rem;
  position: relative;
  bottom: 5rem;
}
}
</style>
