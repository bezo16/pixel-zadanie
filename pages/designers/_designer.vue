<template>
  <section class="designer">
    <main>

    designer number: {{ $route.params.designer }}
      <NuxtLink to="/designers">ZPET</NuxtLink>
      <p>username</p>
      <h2>name</h2>
      <p>email</p>
      <div class="location"></div>
      <p>website</p>
      <div class="moto">
        <h2>title moto</h2>
        <p>value moto</p>
      </div>
    </main>
  </section>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      designer: {} as {},
    }
  }
})
</script>

<style lang="sass" scoped>
  .designer
    padding-top: 200px

  main
    width: 100%
    max-width: 1640px
    margin: 0px auto
    padding-top: 200px
    display: flex
</style>
