<template>
  <header>
    <h1 class="main-title">HuemulShop</h1>
    <p class="legend">Tienda de productos producidos por y para la comunidad <a href="https://www.devschile.cl/">devsChile</a>.</p>
    <nav>
      <ul>
        <li>
          <nuxt-link exact to="/">Inicio</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/stickers">Stickers</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/tazones">Tazones</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/posavasos">Posavasos</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/imanes">Imanes</nuxt-link>
        </li>
        <li>
          <div class="carttotal" v-if="cartCount > 0">{{ cartCount }}</div>
          <nuxt-link to="/cart" class="cart-icon"><img src="https://icongr.am/clarity/shopping-cart.svg?size=24&color=ffffff"></nuxt-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  computed: {
    ...mapGetters(["cartCount"])
  }
};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  padding: 40px 40px 0;
}

.main-title {
  font-size: 60px;
  margin: 0;
}

nav {
  display: flex;
  width: 80vw;
  margin-top: 30px;
  justify-content: center;
  align-items: center;
  border-top: 1px solid #ccc;
  border-bottom: 1px solid #ccc;
  padding: 8px 0;

  ul {
    padding-left: 0;
    li {
      display: inline;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      font-size: 16px;
      padding: 0 20px;
      border-left: 1px solid #ddd;
      border-right: 1px solid #ddd;
      position: relative;
      a {
        color: #49a796;
        font-weight: bold;
        &:hover {
          text-decoration: underline;
        }
      }
    }
  }
}

.cart-icon {
  display: inline-block;

  > img {
    margin-bottom: -5px;
  }
}

.carttotal {
  position: absolute;
  border-radius: 1000px;
  background: #49a796;
  color: white;
  font-size: 10px;
  padding: 3px;
  top: -23px;
  right: 0;
  width: 25px;
  text-align: center;
  height: 25px;
  font-size: 20px;
  padding: 0 8px;
  font-weight: bold;
  text-shadow: 0 0 3px #000;
}

@media screen and (max-width: 850px) {
  h1 {
    margin: 0;
  }
  nav ul li {
    padding: 0 5px !important;
    border-left: none !important;
    border-right: none !important;
  }
}
</style>
