<template>
  <v-toolbar fixed class="teal" dark>
      <v-toolbar-title class="mr-4">
        <!-- <router-link to="/"> -->
          <span class="home" @click="navigateTo({name: 'root'})">
            Day-TabTracker
          </span>
        <!-- </router-link> -->
      </v-toolbar-title>

    <v-toolbar-items>
      <!-- <router-link to=""> -->
        <v-btn flat dark @click="navigateTo({name: 'songs'})">
          Browse
        </v-btn>
      <!-- </router-link> -->
    </v-toolbar-items>

    <v-spacer/>


    <v-toolbar-items>
      <!-- <router-link to="register"> -->
        <v-btn v-if="!$store.state.isUserLoggedIn" flat dark @click="navigateTo({name: 'login'})">
          Log in
        </v-btn>
        <v-btn v-if="!$store.state.isUserLoggedIn" flat dark @click="navigateTo({name: 'register'})">
          Sign Up
        </v-btn>
        <v-btn v-if="$store.state.isUserLoggedIn" flat dark @click="logout">
          Log out
        </v-btn>
      <!-- </router-link> -->
    </v-toolbar-items>

  </v-toolbar>
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    },
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      // TODO: redirect to homepage
      this.$router.push({
        name: 'root'
      })
    }
  }
}

</script>

<style scoped>
  .home {
    cursor: pointer;
  }

  .home:hover {
    color: #e78e
  }

</style>
