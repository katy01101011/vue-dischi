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
          v-for="(item, index) in filteredDiscs"
          :key="index"
          :disc="item"
        />
      </div>
      <div class="found text-center">
        <p>Ho trovato {{ filteredDiscs.length }} album</p>
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
  props: {
    albumsGenres: Array,
    albumsAuthors: Array,
    searchKey: String,
    genreKey: String,
    authorKey: String,
  },
  components: {
    AppLoading,
    AlbumsDisc,
  },
  data: function() {
    return {
      albums: [],
      genres: [],
      authors: [],
      loading: true,
    };
  },

  computed: {
    filteredDiscs: function () {
      const genreKey = this.genreKey;
      const authorKey = this.authorKey;
      let filteredAlbums = this.albums.filter((item) => {
        return item.genre.includes(genreKey);
      });
      let veryFilteredAlbums = filteredAlbums.filter((item) => {
        return item.author.includes(authorKey);
      });
      console.log(filteredAlbums);
      return veryFilteredAlbums;
    },
  },

  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.albums = resp.data.response;
        for (let i = 0; i < this.albums.length; i++) {
          if (!this.genres.includes(this.albums[i].genre)) {
            this.genres.push(this.albums[i].genre)
          }
          if (!this.authors.includes(this.albums[i].author)) {
            this.authors.push(this.albums[i].author)
          }
        }
        this.$emit('albumsGenres', this.genres);
        this.$emit('albumsAuthors', this.authors);
        this.loading = false;
      }
    )
  },
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
      background-color: $primary-color;
      color: $text-primary-color;
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translate(-50%);
      box-shadow: 0px -20px 20px 1px #151515;
      font-size: 1.7rem;
    }
  }
}
</style>
