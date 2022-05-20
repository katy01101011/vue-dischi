<template>
  <div class="discCard p-4 m-2">
    <div class="img-container">
      <img :src="disc.poster" alt="" />
    </div>
    <h3 class="text-uppercase pt-4">{{ disc.title }}</h3>
    <p>{{ disc.author }}</p>
    <p>{{ disc.year }}</p>
  </div>
</template>

<script>
export default {
  name: "AlbumsDisc",
  props: {
    disc: Object,
  },
};
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.discCard {
  background-color: $secondary-color;
  text-align: center;
  border-radius: 12px;
  cursor: pointer;

  &:hover {
    background-color: $card-hover-color;
  }

  &:hover .img-container::after {
    display: inline-block;
  }

  .img-container {
    position: relative;
    img {
      width: 100%;
      border-radius: 7px;
    }

    &::after {
      content: "\25b6";
      font-size: 1.8rem;
      text-align: center;
      line-height: $play-btn;
      color: black;
      position: absolute;
      bottom: 0.5rem;
      right: 0.5rem;
      background-color: $green-color;
      width: $play-btn;
      height: $play-btn;
      border-radius: 50%;
      display: none;
      box-shadow: 2px 2px 8px 0px rgba($color: #000000, $alpha: 0.7);
      cursor: auto;
    }
  }

  h3 {
    color: $text-primary-color;
    font-size: 1.1rem;
  }

  p {
    color: $text-secondary-color;
    line-height: 1.3rem;
    margin: 0;
  }
}
</style>
