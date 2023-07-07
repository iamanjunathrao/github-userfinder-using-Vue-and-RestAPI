<template>
  <v-app>
    <v-app-bar app color="#e7dfd8" dark>
      <v-container>
        <v-app-bar-title>
          <h1 class="page-heading">Github user finder</h1>
        </v-app-bar-title>
      </v-container>
    </v-app-bar>
    <v-main style="background-color: #e7dfd8;">
      <v-container>
        <div class="search-container">
          <search-bar @search="getUserData" />
        </div>
        <user-profile v-if="user" :user="user" />
        <repository-list v-if="repositories" :repositories="repositories" />
        <div class="error-message" v-if="errorMessage">{{ errorMessage }}</div>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import UserProfile from './components/UserProfile.vue';
import RepositoryList from './components/RepositoryList.vue';

export default {
  components: {
    SearchBar,
    UserProfile,
    RepositoryList,
  },
  data() {
    return {
      user: null,
      repositories: null,
      errorMessage: '',
    };
  },
  methods: {
    async getUserData(username) {
      try {
        const response = await axios.get(`https://api.github.com/users/${username}`);
        this.user = response.data;

        const repositoriesResponse = await axios.get(response.data.repos_url);
        this.repositories = repositoriesResponse.data;
      } catch (error) {
        this.errorMessage = 'Error fetching user data. Please try again.';
      }
    },
  },
};
</script>

<style scoped>
@import 'vuetify/dist/vuetify.min.css';

.page-heading {
  color: black;
}

.search-container {
  margin-top: 20px;
}

.error-message {
  color: red;
  margin-top: 10px;
}
</style>
