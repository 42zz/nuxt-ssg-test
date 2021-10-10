<template>
  <div class="index">
    <h1>商品一覧</h1>
    <Products :products="products" />
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, $config }) {
    const products = await $axios.$get(
      `https://${process.env.SHOPIFY_DOMAIN}/admin/api/2021-04/products.json`,
      {
        auth: {
          username: process.env.SHOPIFY_AUTH_USERNAME,
          password: process.env.SHOPIFY_AUTH_PASSWORD
        }
      }
    );
    return products;
  },
};
</script>

<style scoped>
h1 {
  text-align: center;
  
}
</style>