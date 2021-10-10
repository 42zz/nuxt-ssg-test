<template>
  <div class="p-productDetail__wrapper">
    <h1 class="p-productDetail__title">{{ product.title }}</h1>
    <img :src="product.image.src" alt="" />
    <div class="p-productDetail__variants" v-for="(variant, index) in product.variants" :key="index">
      <div class="">{{ variant.price }}円</div>
    </div>
    <div class="p-productDetail__body">{{ product.body_html }}</div>
  <a href="/">一覧に戻る(A)</a>
  <NuxtLink to="/">一覧に戻る(N)</NuxtLink>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $axios, $config, error }) {
    const product = await $axios.$get(
      `https://${process.env.SHOPIFY_DOMAIN}/admin/api/2021-04/products/${params.productId}.json`,
      {
        auth: {
          username: process.env.SHOPIFY_AUTH_USERNAME,
          password: process.env.SHOPIFY_AUTH_PASSWORD
        }
      }
    ).then((response) => {
      return response;
    }).catch((err) => {
      error( err )
    });
    return product;
  },
}
</script>

<style lang="scss" scoped>

img {
  max-width: 100%;
  height: auto;
}

.p-productDetail__wrapper {
  img {
    width: 300px;
  }
}
</style>