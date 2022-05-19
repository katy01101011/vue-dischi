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
header {
  width: 100%;
  height: 100px;
  background-color: gray;
  line-height: 100px;

  img {
    height: 80px;
  }
}
</style>
