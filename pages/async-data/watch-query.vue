<template>
  <div>
    <div v-for="planet in planets" :key="planet.slug">
      <nuxt-link :to="`/async-data/watch-query/${planet.slug}`">
        {{ planet.title }}
      </nuxt-link>
    </div>
    <div class="pt-12">
      Page actuelle : {{ currentPage }}<br />
      <button @click="nextPage">Page suivante</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageBasesIndex',
  async asyncData({ $axios, query }) {
    // eslint-disable-next-line no-console
    console.log('PageBasesIndex asyncData', query)
    const currentPage = query?.currentPage ?? 0
    const planets = await $axios.$get(
      `https://api.nuxtjs.dev/planets?page=${currentPage}`
    )

    return {
      planets,
      currentPage: parseInt(currentPage),
    }
  },
  // watchQuery: ['currentPage'],
  watchQuery(newReq, prevReq) {
    // eslint-disable-next-line no-console
    console.log('PageBasesIndex watchQuery', newReq, prevReq)

    return newReq.currentPage < 3
  },
  methods: {
    nextPage() {
      this.$router.push({
        path: this.$route.path,
        query: { currentPage: this.currentPage + 1 },
      })
    },
  },
}
</script>
