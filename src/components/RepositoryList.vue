<template>
    <div class="repository-list">
      <v-card>
        <v-card-title>Repositories</v-card-title>
        <v-card-text>
          <v-list>
            <v-list-item v-for="repo in repositories" :key="repo.id">
              <v-list-item-title>{{ repo.name }}</v-list-item-title>
              <v-list-item-subtitle>{{ repo.description }}</v-list-item-subtitle>
            </v-list-item>
          </v-list>
        </v-card-text>
      </v-card>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      repositories: {
        type: Array,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .repository-list {
    margin-bottom: 20px;
  }
  </style>
  