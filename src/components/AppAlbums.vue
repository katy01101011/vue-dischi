<template>
  <main>
    <AppLoading v-if="loading" />

    <div v-else class="container">
      <div
        class="
          row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 row-cols-xl-6
          flex-wrap
          justify-content-between
        "
      >
        <AlbumsDisc
          class="p-3"
          v-for="(item, index) in albums"
          :key="index"
          :disc="item"
        />
      </div>
      <div class="found text-center">
        <p>Ho trovato {{ albums.length }} album</p>
      </div>
    </div>
  </main>
</template>

<script>
import AppLoading from "./AppLoading.vue";
import AlbumsDisc from "./AlbumsDisc.vue";
import axios from "axios";

export default {
  name: "AppAlbums",
  components: {
    AppLoading,
    AlbumsDisc,
  },
  data: function () {
    return {
      albums: [],
      loading: true,
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.albums = resp.data.response;
        this.loading = false;
      }
    )
  }
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

main {
  height: calc(100vh - $header-height);
  overflow: auto;
  background-color: $primary-color;
  padding-top: $header-height;

  .container {
    .row {
      margin: auto;
    }

    .found {
      width: 100%;
      height: $foundNumber;
      line-height: $foundNumber;
      background-color: $secondary-color;
      color: $text-primary-color;
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translate(-50%);
      box-shadow: 0px -5px 18px 1px #000000;
    }
  }
}
</style>
