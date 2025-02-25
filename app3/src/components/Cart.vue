<template>
  <div class="cart-container">
    <h2>Cart</h2>
    <div class="cart-item" v-for="(book, index) in cart" :key="index">
      <span>{{ book.title }} - ${{ book.price }}</span>
      <button @click="removeFromCart(index)" class="remove-button">Remove</button>
    </div>
    <div class="total">Total: ${{ totalPrice }}</div>
  </div>
</template>


<script>
export default {
  props: ['cart'],
  computed: {
    totalPrice() {
      return this.cart.reduce((total, book) => total + book.price, 0)
    },
  },
  methods: {
    removeFromCart(index) {
      this.$emit('remove-from-cart', index)
    },
  },
}
</script>


<style scoped>
.cart-container {
  width: 100%;
  max-width: 500px;
  margin-top: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}


.cart-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}


.remove-button {
  background-color: red;
  color: white;
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}


.remove-button:hover {
  background-color: darkred;
}


.total {
  font-weight: bold;
  margin-top: 10px;
}
</style>






