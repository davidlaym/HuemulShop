<template>
  <div id="app">
    <div v-if="cartUIStatus === 'idle'" class="payment">
      <h3>Necesitamos tus detalles de compra:</h3>
      <label for="email">Email</label>
      <br />
      <input id="email" type="email" v-model="stripeEmail" placeholder="usuario@dominio.com" />
      <br />
      <label for="card">Tarjeta de crédito</label>
      <br />
      <card
        class="stripe-card"
        id="card"
        :class="{ complete }"
        stripe="pk_test_5ThYi0UvX3xwoNdgxxxTxxrG"
        :options="stripeOptions"
        @change="complete = $event.complete"
      />
      <button
        class="pay-with-stripe button"
        @click="pay"
        :disabled="!complete || !stripeEmail"
      >Pagar</button>
    </div>

    <div v-else class="statussubmit">
      <div v-if="cartUIStatus === 'failure'">
        <h3>¡Wow!</h3>
        <p>Hubo un error...</p>
        <button @click="clearCart">Intenta nuevamente</button>
      </div>

      <div v-else-if="cartUIStatus === 'loading'" class="loadcontain">
        <h4>Estamos procesando...</h4>
      </div>

      <div v-else-if="cartUIStatus === 'success'" class="loadcontain">
        <h4>¡Bien!</h4>
      </div>
    </div>
  </div>
</template>
 
<script>
import { Card, createToken } from "vue-stripe-elements-plus";

import { mapState } from "vuex";

export default {
  components: { Card },
  computed: {
    ...mapState(["cartUIStatus"])
  },
  data() {
    return {
      complete: false,
      stripeOptions: {
        // you can configure that cc element. I liked the default, but you can
        // see https://stripe.com/docs/stripe.js#element-options for details
      },
      stripeEmail: ""
    };
  },
  methods: {
    pay() {
      createToken().then(data => {
        const stripeData = { data, stripeEmail: this.stripeEmail };
        this.$store.dispatch("postStripeFunction", stripeData);
      });
    },
    clearCart() {
      this.complete = false;
      this.$store.commit("clearCartCount");
    }
  }
};
</script> 
 
<style lang="scss" scoped>
input,
button {
  width: 100%;
}

button {
  margin-top: 20px;
}

.payment {
  margin-top: 20px;
}

.stripe-card {
  margin-top: 10px;
  width: 100%;
  border: 1px solid #ccc;
  padding: 5px 10px;
}

.stripe-card.complete {
  border-color: green;
}
</style> 