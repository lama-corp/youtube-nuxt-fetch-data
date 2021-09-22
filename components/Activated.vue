<template>
  <div>
    Ceci est un composant qui récupère une liste de montagnes via $fetch() !
    <div v-for="mountain in mountains" :key="mountain.slug">
      {{ mountain.title }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Activated',
  data() {
    return {
      mountains: [],
    }
  },
  async fetch() {
    // eslint-disable-next-line no-console
    console.log('Activated fetch()')
    this.mountains = await this.$axios.$get('https://api.nuxtjs.dev/mountains')
  },
  beforeDestroy() {
    // eslint-disable-next-line no-console
    console.log('Activated beforeDestroy()')
  },
  activated() {
    // eslint-disable-next-line no-console
    console.log('Activated activated()')
    // appeler fetch de nouveau si le dernier appel date de plus de 10 secondes
    if (this.$fetchState.timestamp <= Date.now() - 10000) {
      this.$fetch()
    }
  },
}
</script>
