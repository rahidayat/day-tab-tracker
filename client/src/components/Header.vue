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
        <v-btn flat dark>
          Browse
        </v-btn>
      <!-- </router-link> -->
    </v-toolbar-items>

    <v-spacer/>

    <v-toolbar-items>
      <!-- <router-link to="register"> -->
        <v-btn flat dark @click="navigateTo({name: 'register'})">
          Sign Up
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
