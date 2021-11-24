<template>
  <div class="categories-wrapper">
    <div
      class="category"
      v-for="category in categories"
      :key="category.id"
      :style="categoryStyles(category)"
    >
      <div
        class="category__background"
        :style="backgroundStyles(category)"
      ></div>
      <div class="category__content">
        <div class="category__title">{{ category.title }}</div>
        <div class="category__subtitle">Buy Now</div>
      </div>
    </div>
  </div>
</template>


<script>
import categories from "../assets/categories.json";
export default {
  name: "Directory",
  data: function () {
    return { categories };
  },
  methods: {
    categoryStyles: function (category) {
      const isLarge = category.size === "large";
      return { height: isLarge && 380 + "px" };
    },
    backgroundStyles: function (category) {
      return { "background-image": `url(${category.imgURL})` };
    },
  },
};
</script>


<style lang="scss" scoped>
.categories-wrapper {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;

  @media screen and (max-width: 800px) {
    flex-flow: column;
  }
}

.category {
  align-items: center;
  border: 1px solid black;
  display: flex;
  flex: 1 1 auto;
  height: 240px;
  justify-content: center;
  margin: 0 7.5px 15px;
  min-width: 30%;
  overflow: hidden;

  @media screen and (max-width: 800px) {
    height: 200px;
  }

  &:hover {
    cursor: pointer;
  }

  &:hover &__background {
    transform: scale(1.1);
    transition: transform 3s ease;
  }

  &:hover &__content {
    opacity: 0.9;
  }

  &:first-child {
    margin-right: 7.5px;
  }

  &:last-child {
    margin-left: 7.5px;
  }

  &__background {
    background-position: center;
    background-size: cover;
    height: 100%;
    width: 100%;
  }

  &__content {
    align-items: center;
    background: rgba(255, 255, 255, 0.7);
    border: 1px solid #000;
    display: flex;
    flex-direction: column;
    height: 90px;
    justify-content: center;
    padding: 0 25px;
    position: absolute;
  }

  &__title {
    color: #4a4a4a;
    font-size: 22px;
    font-weight: bold;
    margin-bottom: 6px;
    text-transform: uppercase;
  }

  &__subtitle {
    font-size: 16px;
    font-weight: lighter;
  }
}
</style>