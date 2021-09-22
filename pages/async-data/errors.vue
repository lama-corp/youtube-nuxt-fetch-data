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
  async asyncData({ $axios, redirect }) {
    try {
      const mountains = await $axios.$get('https://api.nuxtjs.dev/moudntains')

      return {
        mountains,
      }
    } catch(err) {
      redirect('/')
    }
  },
}
</script>
