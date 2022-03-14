<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Products</router-link> |
      <router-link to="/cart">Cart</router-link>
    </div>
    <router-view/>
    <h4>Carro de la compra</h4>
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
          <button v-on:onclick="añadir" > Añadir </button>
          <button v-on:onclick="eliminar"> Eliminar </button>
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
      cart: [],
    }
  },
  computed: {
    isMock() {
      return process.env.VUE_APP_API_IS_MOCK === "true"
    }
  }
}
</script>
