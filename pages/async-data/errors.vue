<template>
  <div>
    <div v-for="mountain in mountains" :key="mountain.slug">
      {{ mountain.title }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageAsyncDataError',
  async asyncData({ $axios }) {
    const mountains = await $axios.$get('https://api.nuxtjs.dev/mountains')

    return {
      mountains,
    }
  },
  async mounted() {
    // eslint-disable-next-line no-console
    console.log('PageAsyncDataError mounted()')
    await this.$axios.$get(`https://api.nuxtjs.dev/beers/dsqokifsql`)
  },
}
</script>
