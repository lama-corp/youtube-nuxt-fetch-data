<template>
  <div>
    <img :src="beer.image_url" alt="" />
    <div class="pt-12">
      <button @click="goTo('black-label')">Boire une Black Label !</button>
      <br />
      <button @click="goTo('belgian-moon')">Boire une Belgian Moon !</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageBasesBasesId',
  async asyncData({ $axios, params }) {
    // eslint-disable-next-line no-console
    console.log('PageBasesBasesId asyncData()')
    const beer = await $axios.$get(
      `https://api.nuxtjs.dev/beers/${params.basesId}`
    )

    return {
      beer,
    }
  },
  mounted() {
    // eslint-disable-next-line no-console
    console.log('PageBasesBasesId mounted()')
  },
  methods: {
    goTo(id) {
      // eslint-disable-next-line no-console
      console.log('PageBasesBasesId goTo()')
      this.$router.push({
        name: this.$route.name, // async-data-bases-basesId
        params: { basesId: id },
      })
    },
  },
}
</script>
