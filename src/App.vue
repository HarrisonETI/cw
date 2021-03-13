<template>
  <div id="app">
    <header>
      <h1> {{ sitename }}</h1>
          <button @click='showCheckout'>{{this.cart.length}} Checkout</button>
       </header>
       <ProductList @addProduct='addToCart'/>
       <Form :cart='cart' @removeProduct='removeFromCart'/>
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue'
import Form from './components/Form.vue'

export default {
  name: 'App',
  showProduct: true,
  components: {
   ProductList, Form
  },
  data() {
    return {
        sitename: 'After School Lesson',
        cart: []
      }
    },
  methods: {
    
       showCheckout: function(){
        this.showProduct = this.showProduct ? false : true;
                },
      addToCart(product){
        this.cart.push(product)
        alert("Added to cart")
      },
      cartItemCount(){
        return this.cart.length || '';
    },
    removeFromCart(product){
      for(let i=0; i<this.cart.length; i++){
        if(this.cart[i] == product) this.cart.splice(i,1)
      }
    }
  },
}
</script>

 
<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
