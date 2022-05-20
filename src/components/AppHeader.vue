<template>
  <header>
    <a href="">
      <img class="mx-5" src="../assets/logo.svg" alt="" />
    </a>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

header {
  width: 100%;
  height: $header-height;
  background-color: $secondary-color;
  line-height: $header-height;

  img {
    height: $logo-height;
  }
}
</style>
