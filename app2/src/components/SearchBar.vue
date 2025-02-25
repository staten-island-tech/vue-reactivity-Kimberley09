<template>
  <input
    type="text"
    v-model="searchQuery"
    placeholder="Search for a book"
    @input="onSearch"
    class="search-input"
  />
</template>


<script>
export default {
  data() {
    return {
      searchQuery: '',
    }
  },
  methods: {
    onSearch() {
      this.$emit('search', this.searchQuery)
    },
  },
}
</script>


<style scoped>
.search-input {
  padding: 10px;
  margin-bottom: 20px;
  width: 100%;
  max-width: 500px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
</style>


