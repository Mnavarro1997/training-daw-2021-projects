<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Products</router-link> |
      <router-link to="/cart">Cart</router-link>
    </div>
    <router-view/>
    <div> 
      
    <h4>Productos</h4>
    <hr/>
      <div v-for="product, index in products" v-bind:key="product.id" style="display:flex; margin-top: 50px;">
        <div class="imagen">
          <img :src="product.mainImage" alt="img" width="250" height="250">
        </div>
        <div class="datos">
          <div class="idname" style="text-align: left; margin-left: 20px; margin-top: 15px;">
            ID: {{index}} - {{product.name}}
          </div>
          <div class="desc" style="text-align: left; margin-left: 20px; margin-top: 15px;">
            {{product.description}} <br>
          </div>
          <div class="price" style="text-align: left; margin-left: 20px; margin-top: 15px;">
            {{product.price}}€
          </div>
          <b-button variant="outline-primary">View</b-button>
          <b-button variant="outline-primary" style="margin-left: 20px;">Add</b-button>
          <button v-on:onclick="añadir"> Añadir </button>
          <button v-on:onclick="eliminar"> Eliminar </button>
        </div> 
      </div>
  </div>
  </div>
</template>

<script>
export default {
  components: {

  },
    created(){
    fetch('http://localhost:3000/products')
    .then(result => result.json())
    .then(data => this.products = data)
  },

  data() {
    return {
      products: [],
      cart: []
    }
  },
  methods : {
    addCart(){
      var products = []
      products.push(new products())
      alert('deseas añadir al carrito?')

    }
  },
  computed: {
    isMock() {
      return process.env.VUE_APP_API_IS_MOCK === "true"
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
