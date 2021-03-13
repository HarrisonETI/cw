<template>
    <main>
        <div V-if='showProduct'>
            <div v-for="product in products" :key="product.id">
                <figure>
                    <img v-bind:src="product.image">
                </figure>
            <h2>{{product.title}}</h2>
            <p>Price: {{ product.price }}</p>
            <p>Location: {{ product.location }}</p>
            <p>Available stock: {{ product.availableInventory }}</p>
            <button @click="addToCart(product)"  v-if='canAddToCart'>Add to cart</button>
            <button disabled ='disabled' v-else>Add to cart</button>
            </div>
        </div>
    
    </main>
</template>


<script> 
export default {
                name: "ProductList",
                data() {
                    return {
                        showProduct: true,
                          products: [{
                            id: 1001,
                            title: "Math",
                            price: 20,
                            location: "Valletta",
                            image: "product-maths.jpg",
                            availableInventory: 5
                        }],
                    }
                },
                methods: {
                    addToCart(product){
                    console.log(product.title)
                    this.$emit('addProduct', product)
                 },
                  canAddToCart: function(){
                    return this.product.availableInventory > this.cartItemCount;
                },
                 cartItemCount: function(){
                    return this.cart.length || '';
                },
             },
           
}
              
</script>