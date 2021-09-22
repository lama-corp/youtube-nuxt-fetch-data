<template>
  <div>
    <div>Fetch a été appelé {{ nbFetchExecution }} fois !</div>
    <button @click="nextPage">Incrémenter currentPage</button>
  </div>
</template>

<script>
export default {
  name: 'PageFetchQuery',
  data() {
    return {
      nbFetchExecution: 0,
    }
  },
  fetch() {
    this.nbFetchExecution++
  },
  watch: {
    '$route.query.currentPage': {
      handler(currentPage) {
        if (currentPage < 5) this.$fetch()
      },
    },
  },
  methods: {
    nextPage() {
      const currentPage = parseInt(this.$route.query.currentPage ?? 0)

      this.$router.push({
        path: this.$route.path,
        query: { currentPage: currentPage + 1 },
      })
    },
  },
}
</script>
