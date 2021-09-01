<template>
  <div>
    <div v-for="beer in beers" :key="beer.slug">
      <nuxt-link :to="`/async-data/bases/${beer.slug}`">
        {{ beer.name }}
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageBasesIndex',
  // Pour Nuxt < 2.12, utilisez fetch(context)
  // Ex : async fetch({ $axios }) {
  async asyncData({ $axios }) {
    const beers = await $axios.$get('https://api.nuxtjs.dev/beers')

    return {
      beers,
    }
  },
}
</script>
