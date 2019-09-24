<template>
  <div>
    <app-cart-steps />
    <hr />
    <h1 class="center">Tu carro</h1>

    <section v-if="cartUIStatus === 'idle'">
      <app-cart-display />
    </section>

    <section v-else-if="cartUIStatus === 'loading'" class="loader">
      <app-loader />
    </section>

    <section v-else-if="cartUIStatus === 'success'" class="success">
      <h2>¡Bien!</h2>
      <p>Gracias por tu compra, trabajaremos duro para que tengas tus productos lo antes posible en tus manos.</p>
      <button class="pay-with-stripe">
        <nuxt-link exact to="/">Ir al inicio</nuxt-link>
      </button>
    </section>

    <section v-else-if="cartUIStatus === 'failure'">
      <p>Mmmm... algo salió mal. Vuelve a tu carro e intenta nuevamente.</p>
    </section>

    <app-sales-boxes />
  </div>
</template>

<script>
import AppLoader from "~/components/AppLoader.vue";
import AppCartSteps from "~/components/AppCartSteps.vue";
import AppSalesBoxes from "~/components/AppSalesBoxes.vue";
import AppCartDisplay from "~/components/AppCartDisplay.vue";
import { mapState } from "vuex";

export default {
  components: {
    AppCartDisplay,
    AppSalesBoxes,
    AppCartSteps,
    AppLoader
  },
  computed: {
    ...mapState(["cartUIStatus"])
  }
};
</script>

<style lang="scss" scoped>
.loader {
  display: flex;
  justify-content: center;
}

.success {
  text-align: center;
}
</style>