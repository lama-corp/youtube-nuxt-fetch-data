<template>
  <div>
    <keep-alive>
      <Activated v-if="!kill" />
    </keep-alive>
    <div class="pt-12">
      <button v-if="!kill" @click="kill = true">Kill component</button>
      <button v-else @click="kill = false">Restore component</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageFetchActivated',
  data() {
    return {
      kill: false,
    }
  },
  mounted() {
    // eslint-disable-next-line no-console
    console.log('PageFetchActivated mounted()')
  },
}
</script>
