<template>
  <div>
    <h1>Register</h1>
  <input type="email" name="email" value="email" v-model="email">
  <br>
  <input type="password" name="password" value="password" v-model="password">
  <br>
  <div class="error" v-html="error" />
  <br>
  <button @click="register">Register</button>

  </div>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
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
        await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<style scoped>
.error {
  color: red
}

</style>
