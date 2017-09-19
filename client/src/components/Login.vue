<template>
  <v-layout column>
    <v-flex xs6 offset-xs3>
      <Panel title="Login">

        <v-text-field label="E-mail" v-model="email"></v-text-field>
        <v-text-field type="password" label="Password" v-model="password"></v-text-field>

        <div class="error" v-html="error"></div>
        <br>
        <v-btn class="cyan" dark @click="login">Login</v-btn>

      </Panel>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
import Panel from '@/components/Panel'
export default {
  data () {
    return {
      email: 'dayat@mail.com',
      password: '12345678',
      error: null
    }
  },
  // watch: { //just for demo
  //   email (value) {
  //     console.log('email has changed', value)
  //   }
  // },
  methods: {
    async login () {
      try {
        const response = await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  },
  components: {
    Panel
  }
}
</script>

<style scoped>
.error {
  color: red;
}

</style>
