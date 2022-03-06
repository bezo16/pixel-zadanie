<template>
  <section class="designers">
    <div class="search">
      <div class="searchdiv">
        <img src="" alt="search glass">
        <input type="text">
        <button>VYHLEDAT</button>
      </div>
    </div>
    <section class="cards">
      <div v-for="(designer,index) in designers" :key="`designer${index}`" class="card">
        <p>{{ designer.username }}</p>
        <h2>{{ designer.name }}</h2>
        <p>{{ designer.email }}</p>
        <div class="card-location">
          <img src="" alt="" class="card-location--icon">
          <p>{{ designer.address.street }} - {{ designer.address.suite }}</p>
          <p>{{ designer.address.zipcode }} - {{ designer.address.city }}</p>
          <p></p>
        </div>
        <a :href="designer.website">{{ designer.website }}</a>
        <NuxtLink :to="`/designers/${index + 1}`">
          <button class="card-button">ZOBRAZIT PROFIL</button>
        </NuxtLink>
      </div>
    </section>
  </section>
</template>


<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      designers: [] as Array<any>,
    }
  },
  async mounted() {
    this.designers = await this.$axios.$get('https://jsonplaceholder.typicode.com/users')
  }
})
</script>


<style lang="sass" scoped>
  .designers
    margin-top: 200px
    background-color: #ecefff

  .search
    max-width: 1000px
    margin: 0px auto

  .cards
    max-width: 1500px
    margin: 0 auto
    display: flex
    flex-wrap: wrap
    justify-content: center
    padding-bottom: 100px

  .card
    width: 450px
    margin: 20px
    padding: 25px
    border-radius: 25px
    background: white

  .card-button
    background-color: black

</style>
