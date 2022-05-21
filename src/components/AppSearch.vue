<template>
  <div>
    <select class="form-select" aria-label="Default select example">
      <option value="1" v-for="(genre, index) in genres" :key="index">{{ genre }}</option>

    </select>
  </div>
</template>

<script>
export default {
  name: "AppSearch",
  props: {
    genres: Array
  }
};
</script>

<style lang="scss" scoped></style>
