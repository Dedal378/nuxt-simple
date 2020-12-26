<template>

  <header>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <nuxt-link class="navbar-brand" to="#">NUXT JS</nuxt-link>

      <div class="collapse navbar-collapse">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <nuxt-link active-class="active" class="nav-link" exact to="/">Home</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link active-class="active" class="nav-link" no-prefetch to="/users">Users</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link active-class="active" class="nav-link" no-prefetch to="/about">About</nuxt-link>
          </li>
          <li v-if="!isAuth" class="nav-item">
            <nuxt-link active-class="active" class="nav-link" no-prefetch to="/login">Login</nuxt-link>
          </li>
          <li v-else class="nav-item">
            <a class="nav-link" href="#" @click.prevent="logout">Logout</a>
          </li>
        </ul>
      </div>
    </nav>
  </header>

</template>

<script>
export default {
  computed: {
    isAuth () {
      return this.$store.getters.isAuth
    }
  },
  methods: {
    logout () {
      this.$store.dispatch('logout')
      this.$router.push('/login')
    }
  }
}
</script>
