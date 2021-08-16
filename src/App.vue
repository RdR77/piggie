<template>
  <div id="app">
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="14" offset="0">
          <Home
            @paginate="homePaginate"
            v-if="productos.length"
            :productosList="productos"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Home,
  },
  data() {
    return {
      productos: [],
    };
  },
  mounted: function () {
    axios
      .get("http://localhost:3000/products?perpage=5")
      .then((response) => (this.productos = response.data));
  },
  methods: {
    homePaginate(page) {
      axios
        .get("http://localhost:3000/products?perpage=5&page=" + page)
        .then((response) => (this.productos = response.data));
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
