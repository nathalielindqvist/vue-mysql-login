<template>
  <div>
    <h1>Sign Up</h1>
    <p>By signing up you accept that your user information is stored in a database.</p>
    <div class="input-all">
    <div>
    <b-form-input type="email" placeholder="Email" v-model="email" />
    </div>
    <div>
    <b-form-input type="password" placeholder="Password" v-model="password" />
    </div>
    <div>
    <b-form-input type="password" placeholder="Password (repeat)" v-model="password_repeat" />
    </div>
    </div>
    <b-button variant="success" @click="signUp" value="Sign Up">Sign up</b-button>
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
      password_repeat: '',
      msg: ''
    };
  },
  methods: {
    async signUp() {
      try {
        const credentials = {
          email: this.email,
          password: this.password,
          password_repeat: this.password_repeat
        };
        const response = await AuthService.signUp(credentials);
        this.msg = response.msg;
      } catch (error) {
        this.msg = error.response.data.msg;
      }
    }
  }
};
</script>