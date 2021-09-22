<template>
  <div>
    <div v-for="item in items" :key="item.slug">
      {{ item.title }}
    </div>
    <div class="pt-12">
      <button
        type="button"
        class="bg-rose-600"
        :disabled="$fetchState.pending"
        @click="$fetch"
      >
        <span v-if="$fetchState.pending">
          <IconSpinner class="animate-spin h-6 w-6 float-left mr-3" />
          En cours
        </span>
        <span v-else>Rafraîchir les données</span>
      </button>
    </div>
  </div>
</template>

<script>
import IconSpinner from 'assets/icons/icon-spinner.svg?inline'

// Disponible sur NuxtJS version 2.12 et +
export default {
  name: 'PageFetchIndex',
  components: {
    IconSpinner,
  },
  data() {
    return {
      modulo: 0,
      items: [],
    }
  },
  async fetch() {
    console.log('PageFetch fetch()')
    const objectType = this.modulo % 2 === 0 ? 'planets' : 'mountains'
    this.items = await this.$axios.$get(`https://api.nuxtjs.dev/${objectType}`)
    this.modulo++
  },
  fetchOnServer: true,
  // fetchOnServer() { return true }
}
</script>
