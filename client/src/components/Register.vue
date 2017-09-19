<template>
  <v-layout column>
    <v-flex xs6 offset-xs3>
      <Panel title="Register">
        
        <form name="daytracker-form" autocomplete="off">
          <v-text-field label="E-mail" v-model="email"></v-text-field>
          <v-text-field type="password" label="Password" v-model="password" autocomplete="new-password"></v-text-field>
        </form>
        <div class="error" v-html="error"></div>
        <br>
        <v-btn class="cyan" dark @click="register">Register</v-btn>

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
      email: 'abc',
      password: '123',
      error: null
    }
  },
  // watch: { //just for demo
  //   email (value) {
  //     console.log('email has changed', value)
  //   }
  // },
  methods: {
    async register () {
      try {
        const response = await AuthenticationService.register({
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
