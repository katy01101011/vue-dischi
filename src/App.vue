<template>
  <div>
    <AppHeader />
    <AppAlbums />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppAlbums from "./components/AppAlbums.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    AppAlbums,
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
</style>
