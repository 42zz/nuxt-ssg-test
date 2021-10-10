<template>
  <section class="p-product__list">
    <a
      :href="`/product/${product.id}`"
      class="p-product__item"
      v-for="(product, index) in products"
      :key="index"
    >
      <h2 class="p-product__title">{{ product.title }}</h2>
      <img :src="product.image.src" alt="" />
    </a>
  </section>
</template>

<script>
export default {
  props: ["products"]
};
</script>

<style lang="scss">
img {
  max-width: 100%;
  height: auto;
}
.p-product {
  &__list {
    display: flex;
    align-items: flex-start;
    flex-wrap: wrap;
  }
  &__item {
    width: 30%;
    margin-right: 2%;
    box-shadow: 0 6px 10px rgba(0, 0, 0, 0.4);
    display: block;
    text-decoration: none;
    img {
      width: 100%;
      height: 300px;
      object-fit: cover;
      vertical-align: bottom;
    }
  }
  &__title {
    text-align: center;
    font-size: 18px;
    color: #6b413c;
  }
}
</style>