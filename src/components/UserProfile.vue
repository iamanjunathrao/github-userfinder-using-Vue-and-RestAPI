<template>
  <div class="user-profile">
    <v-card>
      <v-card-title>
        <h2>{{ user.name }}</h2>
      </v-card-title>
      <v-card-text>
        <div class="user-avatar">
          <img :src="user.avatar_url" alt="User Avatar" />
        </div>
        <div class="user-bio">{{ user.bio }}</div>
        <div class="user-details">
          <p><strong>Followers:</strong> {{ user.followers }}</p>
          <p><strong>Repositories:</strong> {{ user.public_repos }}</p>
        </div>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.user-profile {
  margin-bottom: 20px;
}

.user-avatar {
  width: 100px;
  height: 100px;
  margin-bottom: 10px;
}

.user-avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
}

.user-bio {
  margin-bottom: 10px;
}

.user-details p {
  margin: 5px 0;
}
</style>
