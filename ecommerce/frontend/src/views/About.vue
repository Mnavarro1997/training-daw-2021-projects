<template>
  <div class="about">
    <h1>This is an about page</h1>
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
        </div> 
      </div>
  </div>
  
</template>
