<template>
  <section>

    <h1>Error 404</h1>
    <nuxt-link :to="'/'">Home</nuxt-link>

  </section>
</template>

<script>
  export default {
    name: "error"
  }
</script>

<style scoped>

  section {
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  h1 {
    color: red;
  }

</style>
