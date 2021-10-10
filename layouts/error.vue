<template>
  <div class="">
    <h1>{{ error.statusCode }}</h1>
    <p>{{ error.message }}</p>
  </div>
</template>

<script>
export default {
  props: {
    error: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  mounted() {
    console.log(this.error);
  }
};
</script>

<style>
</style>