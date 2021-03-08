<template>
  <div>
    <h1>Login</h1>
    <div class="input-all">
    <div>
    <b-form-input type="email" placeholder="Email" v-model="email" />
    </div>
    <div>
    <b-form-input type="password" placeholder="Password" v-model="password" />
    </div>
    </div>
    <b-button variant="success" @click="login" value="Login">Login</b-button>
    <p v-if="msg">{{ msg }}</p>
  </div>
</template>

<script>
import AuthService from '@/services/AuthService.js';

export default {
  data() {
    return {
      email: '',
      password: '',
      msg: ''
    };
  },
  methods: {
    async login() {
      try {
        const credentials = {
          email: this.email,
          password: this.password
        };
        const response = await AuthService.login(credentials);
        this.msg = response.msg;
        const token = response.token;
        const user = response.user;
        this.$store.dispatch('login', { token, user });
        this.$router.push('/');
      } catch (error) {
        this.msg = error.response.data.msg;
      }
    }
  }
};
</script>