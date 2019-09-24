<template>
  <div>
    <app-featured-products />
  </div>
</template>

<script>
import AppSalesBoxes from "~/components/AppSalesBoxes.vue";
import AppFeaturedProducts from "~/components/AppFeaturedProducts.vue";

export default {
  components: {
    AppSalesBoxes,
    AppFeaturedProducts
  }
};
</script>

<style>
.test {
  margin: 3vh;
}

main {
  width: 75vw;
}
</style>
