<template>
  <section>
    <div class="shopping">
      <h2 :class="{ active: cartUIStatus === 'idle' && cartCount === 0 }">01</h2>
      <h4>Tu Carro</h4>
    </div>
    <div class="checkout">
      <h2 :class="{ active: cartUIStatus === 'idle' && cartCount > 0 }">02</h2>
      <h4>¡Paga!</h4>
    </div>
    <div class="order">
      <h2 :class="{ active: cartUIStatus === 'success' }">03</h2>
      <h4>¡Tamos Listos!</h4>
    </div>
  </section>
</template>

<script>
import { mapState } from "vuex";
import { mapGetters } from "vuex";

export default {
  computed: {
    ...mapState(["cartUIStatus"]),
    ...mapGetters(["cartCount"])
  }
};
</script>

<style lang="scss" scoped>
section {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: 1fr;
  grid-column-gap: 100px;
  grid-row-gap: 0px;
  text-align: center;
  width: 80%;
  margin: 20px auto 0;
  div {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

h2 {
  width: 80px;
  height: 80px;
  border-radius: 1000px;
  border: 1px solid #ccc;
  padding-top: 21px;
  color: #555;
  &.active {
    background: #49a796;
    border: 1px solid #49a796;
    color: white;
  }
}

h4 {
  margin-top: 20px;
  color: #555;
}

@media screen and (max-width: 600px) {
  section {
    grid-column-gap: 30px !important;
  }
}
</style>