<template>
  <section>

    <h1>{{ pageTitle }}</h1>

    <ul>
      <li v-for="user in users" :key="user.id">
        <a href="#" @click.prevent="goTo(user)">{{ user.name }} ({{ user.email }})</a>
      </li>
    </ul>

  </section>
</template>

<script>
export default {
  name: "Users",
  // загрузка асинхронных данных: два способа:
  // asyncData исполняется только на сервере, без доступа к this, тк всё на сервере

  // опускаем оба способа, потому что при создании приложения
  // с помощью nuxtServerInit оправили запрос fetchUsers и стор у нас уже записался данными

/*  async asyncData ({ store, error }) {
    try {
      await store.dispatch('users/fetchUsers')
      return {}
    } catch (e) {
      error(e)
    }
  },*/

/*  async fetch ({ store, error }) {
    try {
      if (store.getters['users/users'].length === 0) {
        await store.dispatch('users/fetchUsers')
      }
    } catch (e) {
      error(e)
    }
  },*/

  data () {
    return { pageTitle: 'Users page' }
  },
  computed: {
    users () {
      return this.$store.getters['users/users']
    },
  },
  methods: {
    goTo (user) {
      this.$router.push(`/users/${user.id}`)
    },
  }
}
</script>

<style scoped>

</style>
