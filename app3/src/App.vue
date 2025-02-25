<template>
  <div id="app" class="app-container">
    <SearchBar @search="updateSearchQuery" />
    <BookList :searchQuery="searchQuery" @add-to-cart="addToCart" />
    <Cart :cart="cart" @remove-from-cart="removeFromCart" />
  </div>
</template>


<script>
import SearchBar from './components/SearchBar.vue'
import BookList from './components/BookList.vue'
import Cart from './components/Cart.vue'


export default {
  name: 'App',
  components: {
    SearchBar,
    BookList,
    Cart,
  },
  data() {
    return {
      searchQuery: '',
      cart: [],
    }
  },
  methods: {
    updateSearchQuery(query) {
      this.searchQuery = query
    },
    addToCart(book) {
      this.cart.push(book)
    },
    removeFromCart(index) {
      this.cart.splice(index, 1)
    },
  }
}
</script>


<style>
.app-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  font-family: Arial, sans-serif;
}
</style>