<template>
  <div>
    <header>
      <a href="">
        <img class="mx-5" src="./assets/logo.svg" alt="" />
      </a>
      <nav>
        <template v-if="clicked">
          <AppSearch v-for="(arrays, index) in selectData"
          :key="index"
          :albumInfo="arrays"
          @search="saveWord($event)"
          :searchKey="searchKey" />
        </template>
        <img @click="isClicked"
        v-if="clicked === false"
        class="searchIcon mx-5"
        src="./assets/search.svg"
        alt="" />
        <img @click="isClicked"
        v-else class="backIcon mx-5"
        src="./assets/back.svg"
        alt="" />
      </nav>
    </header>
    <AppAlbums @albumsGenres="selectGenres"
    @albumsAuthors="selectAuthors" 
    :genreKey="this.searchGenre"
    :authorKey="this.searchAuthor"
    />
  </div>
</template>

<script>
import AppAlbums from "./components/AppAlbums.vue";
import AppSearch from "./components/AppSearch.vue";

export default {
  name: "App",

  data: function() {
    return {
      clicked: false,
      selectData: [],
      searchKey: [],
      searchGenre: "",
      searchAuthor: "",
    }
  },

  components: {
    AppSearch,
    AppAlbums,
  },

  methods: {
    isClicked: function() {
      this.clicked = !this.clicked;
    },
    selectGenres(value) {
      this.selectData.push(value);
    },
    selectAuthors(value) {
      this.selectData.push(value);
      console.log(this.selectData);
    },
    saveWord: function(myKey) {
      if (this.selectData[0].includes(myKey)) {
        this.searchGenre = myKey
      } else {
        this.searchAuthor = myKey
      }
      console.log(this.searchGenre);
      console.log(this.searchAuthor);
    },
  }
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

    nav {
      display: flex;
      align-items: center;

      img {
        width: 3rem;
        cursor: pointer;

        &:hover {
          filter: invert(20%);
        }
      }
    }
  }
}
</style>
