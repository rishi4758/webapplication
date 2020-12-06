<template>
  <header>
    <div class="header">
      <div class="logo"><nuxt-link exact to="/">ShoeStore</nuxt-link></div>
      <div><search-bar></search-bar></div>
      <div class="menu">
        <li>
          <nuxt-link exact to="/" class="link">Home</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/all" class="link">All</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/women" class="link">Women</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/men" class="link">Men</nuxt-link>
        </li>
        <li>
          <div class="carttotal" v-if="cartCount > 0">{{ cartCount }}</div>
          <nuxt-link to="/cart" class="link">Cart</nuxt-link>
        </li>
      </div>
    </div>
  </header>
</template>

<script>
import { mapGetters } from "vuex";
import SearchBar from "./SearchBar/SearchBar";

export default {
  components: {
    SearchBar,
  },
  computed: {
    ...mapGetters(["cartCount"]),
  },
};
</script>

<style lang="scss" scoped>
.header {
  background-color: #000;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  opacity: 0.9;
  height: 80px;
  width: 100%;
  top: 0;
  margin-bottom: 50px;
}
.menu {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 600px;
  margin-right: 50px;
}
.logo {
  color: #fff;
  font-weight: 900;
  font-size: 40px;
  margin-left: 50px;
  display: flex;
  margin-top: 10px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.link {
  text-align: center;
  color: #fff;
  font-weight: 700;
  font-family: Arial, Helvetica, sans-serif;
  height: 25px;
  font-size: 18px;
  transition: 0.1s ease-in-out;
  text-decoration: none;
}

li {
  width: 150px;
  text-align: center;
}
li:hover {
  background-color: #000;
  border: solid #fff 1px;
  border-radius: 1px;
}

.carttotal {
  position: absolute;
  border-radius: 1000px;
  background: black;
  color: white;
  font-size: 10px;
  padding: 3px;
  top: -18px;
  right: -5px;
  width: 25px;
  text-align: center;
  height: 25px;
  font-size: 10px;
  padding: 6px 10px;
  font-weight: bold;
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
