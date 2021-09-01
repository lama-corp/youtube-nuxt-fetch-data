<template>
  <div>
    <div v-for="mountain in mountains" :key="mountain.slug">
      {{ mountain.title }}
    </div>
    <div class="pt-12">
      <button @click="$fetch">Refresh Page</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageFetchDelay',
  data() {
    return {
      mountains: [],
    }
  },
  async fetch() {
    // eslint-disable-next-line no-console
    console.log('PageFetchDelay fetch()')
    this.mountains = await this.$axios.$get('https://api.nuxtjs.dev/mountains')
  },
  fetchDelay: 5000,
}
</script>
