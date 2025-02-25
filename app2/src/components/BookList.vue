<template>
  <div class="book-list">
    <div class="book-card" v-for="book in filteredBooks" :key="book.title">
      <span>{{ book.title }} - ${{ book.price }}</span>
      <button @click="addToCart(book)" class="add-button">Add to Cart</button>
    </div>
  </div>
</template>


<script>
import { books } from '../books'


export default {
  props: ['searchQuery'],
  data() {
    return {
      books,
    }
  },
  computed: {
    filteredBooks() {
      return this.books.filter((book) =>
        book.title.toLowerCase().includes(this.searchQuery.toLowerCase()),
      )
    },
  },
  methods: {
    addToCart(book) {
      this.$emit('add-to-cart', book)
    },
  },
}
</script>


<style scoped>
.book-list {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}


.book-card {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  width: 250px;
  text-align: center;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}


.add-button {
  background-color: green;
  color: white;
  padding: 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}


.add-button:hover {
  background-color: darkgreen;
}
</style>


