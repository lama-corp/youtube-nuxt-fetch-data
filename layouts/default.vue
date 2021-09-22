<template>
  <div class="header">
    <div class="p-4">
      <nuxt-link
        v-for="link in links"
        :key="link.name"
        :to="{ name: link.name }"
        class="mr-3"
      >
        <strong>{{ link.label }}</strong>
        <span v-if="link.subLabel"> : {{ link.subLabel }}</span>
      </nuxt-link>
    </div>
    <div class="pt-12">
      <Nuxt />
    </div>
  </div>
</template>

<script>
export default {
  name: 'LayoutDefault',
  // Ceci n'est jamais exécuté
  asyncData() {
    // eslint-disable-next-line no-console
    console.log('ASYNCDATA LAYOUT')
  },
  data() {
    return {
      links: [
        { name: 'index', label: 'Home' },
        { name: 'async-data-bases', label: 'Async Data', subLabel: 'bases' },
        { name: 'async-data-errors', label: 'Async Data', subLabel: 'erreurs' },
        {
          name: 'async-data-watch-query',
          label: 'Async Data',
          subLabel: 'watch-query',
        },
        { name: 'fetch-bases', label: 'Fetch', subLabel: 'bases' },
        { name: 'fetch-activated', label: 'Fetch', subLabel: 'hook activated' },
        { name: 'fetch-delay', label: 'Fetch', subLabel: 'délai' },
        { name: 'fetch-layout', label: 'Fetch', subLabel: 'layout' },
        { name: 'fetch-query', label: 'Fetch', subLabel: 'query' },
        { name: 'fetch-error', label: 'Fetch', subLabel: 'erreurs' },
      ],
    }
  },
}
</script>

<style scoped>
a {
  @apply inline-flex items-center px-2.5 py-1.5 border border-transparent text-xs font-medium rounded shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500;
}
</style>
