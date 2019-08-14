<template>

  <div class="container">
    <div class="row">
      <div class="col-md-7">

        <div class="row">
          <div :key="product.id" class="col-md-6" v-for="product in products">

            <product :IsInCart="IsInCart(product)" v-on:add-to-cart="addToCart(product)" :product="product"></product>
            
          </div>
        </div>
        
      </div>
      <div class="col-md-5 my-5">
        <cart v-on:pay="pay()" v-on:remove-from-cart="RemoveFromCart($event)" :products="cart"></cart>
        
      </div>
    </div>
  </div>
  
</template>

<script>

import products from '@/products.json'
import Product from '@/components/Product.vue'
import Cart from '@/components/Cart.vue'

export default {
  name: 'app',

  components: {
    Product,
    Cart
  },

  data() {

    return {

      products,

      cart: []
      
    }
  },

  methods: {

    addToCart(product){
      this.cart.push(product)
      //console.log(product)
    },
    IsInCart(product) {
      const item = this.cart.find(item => item.id === product.id)

      if(item) {
        return true;
      }

      return false
    },
    RemoveFromCart(product){
      this.cart = this.cart.filter(item => item.id !== product.id)
    },
    pay(){

      this.cart = [];
      alert('Shopping completed !')
    }
  }
  
}
</script>


<style>
  body{
    background-color: #FFF;
  }
</style>


