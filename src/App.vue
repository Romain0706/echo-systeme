<template>
  <div>
    <router-link :to="'/'">Home</router-link>
    <button v-if="!authenticated" @click="login()">Log In</button>
    <button v-if="authenticated" @click="logout()">Log Out</button>

    <div class="container">
      <router-view :auth="auth" :authenticated="authenticated">
        <!-- CONTENU DE LA PAGE LOADER ICI -->
      </router-view>
    </div>
  </div>
</template>

<script>
import AuthService from './auth/AuthService'
const auth = new AuthService()
const { login, logout, authenticated, authNotifier } = auth
export default {
  name: 'app',
  data () {
    authNotifier.on('authChange', authState => {
      this.authenticated = authState.authenticated
    })
    return {
      auth,
      authenticated
    }
  },
  methods: {
    login,
    logout
  }
}
</script>

<style lang="scss">
  @import './scss/main.scss';
</style>
