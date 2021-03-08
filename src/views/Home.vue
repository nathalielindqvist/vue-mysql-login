<template>
  <div>
    <h1>You made it in!</h1>
    <div class="secret-text">
        <p>Glad to have you on board. Only logged in users can see this page, so let's keep it a secret! It's not much, but it's home.</p>
      </div>
      <div id="gif">
        <iframe src="https://giphy.com/embed/l0HlHFRbmaZtBRhXG" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
      </div>
    <b-button variant="success" value="Logout" @click="logout">Log out</b-button>
  </div>
</template>

<script>
import AuthService from '@/services/AuthService.js';

export default {
  data() {
    return {
      secretMessage: '',
      username: ''
    };
  },
  async created() {
    if (!this.$store.getters.isLoggedIn) {
      this.$router.push('/login');
    }
    this.username = this.$store.getters.getUser.username;
    this.secretMessage = await AuthService.getSecretContent();
  },
  methods: {
    logout() {
      this.$store.dispatch('logout');
      this.$router.push('/login');
    }
  }
};
</script>