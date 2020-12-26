<template>
  <div>

    <h1>{{ user.name }}</h1>
    <hr />
    <strong>{{ user.email }}</strong>

  </div>
</template>

<script>
export default {
  validate ({ params }) {
    return /^\d+$/.test(params.id)
  },
  async asyncData ({ params, error, store }) {
    try {
      const user = await store.dispatch('users/fetchUserByID', params.id)
      return { user }
    } catch (e) {
      error(e)
    }
  }
}
</script>

<style scoped>

</style>
