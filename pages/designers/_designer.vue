<template>
  <section class="designer">
    <main v-if="designer.name">
      <NuxtLink to="/designers">ZPET</NuxtLink>
      <p>{{ designer.username }}</p>
      <h2>{{ designer.name }}</h2>
      <p>{{ designer.email }}</p>
      <div class="location">
        <p>{{ designer.address.street }} {{ designer.address.suite }}</p>
        <p>{{ designer.address.zipcode }} - {{ designer.address.city }}</p>
      </div>
      <p>{{ designer.website }}</p>
      <div class="moto">
        <h2>{{ designer.company.name }}</h2>
        <p>{{ designer.company.catchPhrase }}</p>
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
  },
  async mounted() {
    const designerId = this.$route.params.designer
    this.designer = await this.$axios.$get(`https://jsonplaceholder.typicode.com/users/${designerId}`)
  }
})
</script>

<style lang="sass" scoped>
  .designer
    padding-top: 200px

  main
    width: 100%
    min-height: calc(100vh - 10rem - 200px)
    max-width: 1640px
    margin: 0px auto
    padding-top: 200px
    display: flex
    flex-direction: column
</style>
