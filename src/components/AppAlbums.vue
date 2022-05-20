<template>
  <main>
    <div v-if="loading" class="container">
      <AppLoading />
    </div>
    <div v-else class="container">
      <div
        class="row row-cols-2 row-cols-sm-3 row-cols-md-4 row-cols-lg-5 row-cols-xl-6 flex-wrap justify-content-between"
      >
        <AlbumsDisc
          class="p-3"
          v-for="(item, index) in albums"
          :key="index"
          :disc="item"
        />
      </div>
    </div>
  </main>
</template>

<script>
import AppLoading from "./AlbumsDisc.vue";
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
      });
  },
};
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
  }
}
</style>
