<template>
  <section>

    <div v-if="$route.query.message" class="alert alert-danger mb-3">
      Need login first
    </div>

    <form @submit.prevent="onSubmit">
      <h1>Login</h1>

      <div class="form-group">
        <input class="form-control" type="text">
      </div>

      <div class="form-group">
        <input class="form-control" type="password">
      </div>

      <p><nuxt-link to="/">Home</nuxt-link></p>
      <button class="btn btn-primary" type="submit">Login</button>
    </form>

  </section>
</template>

<script>
export default {
  name: 'login',
  layout: 'empty',
  methods: {
    onSubmit () {
      this.$store.dispatch('login')
      this.$router.push('/')
    }
  }
}
</script>

<style scoped>
form {
  width: 600px;
}
</style>
