<template>
  <div>
    <p v-if="$fetchState.pending">Fetching mountains...</p>
    <p v-else-if="$fetchState.error">
      An error occurred :(<br />
      {{ $fetchState.error }}
    </p>
    <div v-else>
      <h1>Nuxt Mountains</h1>
      <ul>
        <li v-for="mountain in mountains" :key="mountain.slug">
          {{ mountain.title }}
        </li>
      </ul>
      <button @click="$fetch">Refresh</button>
    </div>
  </div>
</template>

<script>
// Exemple copié / collé de la documentation
export default {
  name: 'PageFetchError',
  data() {
    return {
      mountains: [],
    }
  },
  async fetch() {
    // this.mountains = await this.$axios.$get('https://api.nuxtjs.dev/mountains')
    try {
      this.mountains = await this.$axios.$get('https://apsi.nuxtjs.dev/moutains')
    } catch (err) {
      if (process.server) {
        this.$nuxt.context.redirect('/')
      } else {
        throw err
      }
    }
  },
}
</script>
