<template>
  <div>
    <select class="form-select" aria-label="Default select example">
      <option :value="albumInfo[index]" v-for="(array, index) in albumInfo" :key="index">{{ albumInfo[index] }}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "AppSearch",
  props: {
    albumInfo: Array
  },
};
</script>

<style lang="scss" scoped></style>
