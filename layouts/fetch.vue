<template>
  <div>
    <nuxt-link to="/">Home</nuxt-link>
    <Nuxt />
  </div>
</template>

<script>
export default {
  name: 'LayoutFetch',
  fetch() {
    console.log('LayoutFetch fetch()')
  },
  // fetchOnServer: false,
}
</script>
