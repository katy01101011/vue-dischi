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
@import "~@fontsource/montserrat/400.css";
@import "~@fontsource/montserrat/700.css";

body {
  font-family: "Montserrat", Helvetica, sans-serif;
}
</style>
