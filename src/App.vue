<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/sign-up">Sign up</router-link> |
      <router-link to="/login">Login</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
import Vue from 'vue'
import { BootstrapVue } from 'bootstrap-vue'
import './style.scss'
Vue.use(BootstrapVue)
export default {

}
</script>
