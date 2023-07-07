<template>
    <div class="search-bar">
      <v-text-field v-model="searchQuery" label="Search for a GitHub user" @keyup.enter="searchUser" outlined></v-text-field>
    </div>
  </template>
  
  <script>
  export default {
  name: 'SearchBar', // Add the name property
  data() {
    return {
      searchQuery: '',
    };
  },
  methods: {
    searchUser() {
      // Call a method in the parent component to handle the search query
      this.$emit('search', this.searchQuery);
    },
  },
};
  </script>
  
  <style scoped>
  .search-bar {
    margin-bottom: 20px;
  }
  </style>
  