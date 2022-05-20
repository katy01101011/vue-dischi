<template>
  <div>
    <header>
      <a href="">
        <img class="mx-5" src="./assets/logo.svg" alt="" />
      </a>
      <nav>
        <AppSearch />
      </nav>
    </header>
    <AppAlbums />
  </div>
</template>

<script>
import AppAlbums from "./components/AppAlbums.vue";
import AppSearch from "./components/AppSearch.vue";

export default {
  name: "App",
  components: {
    AppSearch,
    AppAlbums,
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";
@import "~@fontsource/montserrat/400.css";
@import "~@fontsource/montserrat/700.css";

@import "./style/variables.scss";

body {
  font-family: "Montserrat", Helvetica, sans-serif;

  header {
    width: 100%;
    height: $header-height;
    background-color: $secondary-color;
    line-height: $header-height;
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
      height: $logo-height;
    }
  }
}
</style>
