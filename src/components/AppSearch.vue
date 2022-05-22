<template>
  <select class="form-select ms-4" aria-label="Default select example" v-model="inputChoice" @change="$emit('search', inputChoice)">
    <option value="">Tutti</option>
    <option :value="albumInfo[index]" v-for="(array, index) in albumInfo" :key="index">{{ albumInfo[index] }}</option>
  </select>
</template>

<script>
export default {
  name: "AppSearch",
  data: function() {
    return {
      inputChoice: "",
    }
  },
  props: {
    albumInfo: Array
  },
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

  select {
    width: $select-width;
    height: $select-height;
    border-radius: calc($select-height / 2);
    padding-left: 2rem;
  }
</style>
