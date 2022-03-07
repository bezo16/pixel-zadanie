<template>
  <div>
    <Nuxt />
    <TheFooter />
    <TheTopBar />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  methods: {
    log() {
      console.log('key was pressed')
    }
  }
})
</script>

<style lang="sass" scoped>
  html
    font-family: 'Montserrat', sans-serif

</style>
