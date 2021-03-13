<script>
export default {
    name: 'form',
    props: ['cart'],
    data() {
        return {
            name: '',
            address: '',
        }
    },
    methods: {
        removeProduct(product) {
            this.$emit('removeProduct', product)
            alert("Product removed")
        }
    },
}
</script>

<template>
    <div>
    <h2>Checkout</h2>
    <h3>Added products</h3>
    <div v-for='(product, index) in cart' :key="index">
        {{product.title}} <button @click="removeProduct(product)">remove</button>
    </div>
    <p>
        <strong> Name </strong> <input v-model="name" />
        <strong> Address </strong> <input v-model="address" />
        <button> Submit </button>
    </p>
    </div>
</template>
