<template>
  <section class="designers">
    <div class="search">
      <div class="searchdiv">
        <!-- <img src="" alt="search glass">  -->
        <input class="search-input" placeholder="Vyhladavanie" type="text" v-model="searchQuery" @input="filterDesigners">
      </div>
        <button class="search-button btncurve">VYHLEDAT</button>
    </div>
    <section class="cards">
      <div v-for="(designer,index) in designers" :key="`designer${index}`" class="card">
        <p class="card-username">{{ designer.username }}</p>
        <h2 class="card-name">{{ designer.name }}</h2>
        <p class="card-email">{{ designer.email }}</p>
        <div class="card-location">
          <img src="~/assets/img/location.svg" alt="" class="card-location--icon">
          <p class="card-city">{{ designer.address.city }}</p>
          <p class="card-street">{{ designer.address.street }} - {{ designer.address.suite }}</p>
          <p class="card-address">{{ designer.address.zipcode }} - {{ designer.address.city }}</p>
        </div>
        <a class="card-website" :href="designer.website">{{ designer.website }}</a>
        <NuxtLink :to="`/designers/${index + 1}`">
          <button class="card-button btncurve">ZOBRAZIT PROFIL --></button>
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
      allDesigners: [] as Array<any>,
      designers: [] as Array<any>,
      searchQuery: '' as string,
    }
  },
  methods: {
     filterDesigners() {
       this.designers = this.allDesigners.filter(designer => designer.name.toLowerCase().includes(this.searchQuery.toLowerCase()))
     }
  },
  async mounted() {
    this.allDesigners = await this.$axios.$get('https://jsonplaceholder.typicode.com/users')
    this.designers = this.allDesigners
  }
})
</script>


<style lang="sass" scoped>
  .designers
    margin-top: 300px
    background-color: #ecefff

  .search
    max-width: 750px
    width: 90%
    background-color: white
    padding: 22px
    height: 100px
    position: relative
    transform: translateY(-50%)
    margin: 0px auto
    box-shadow: 1px 1px 16px 3px rgba(0,0,0,0.15)
    display: flex
    z-index: 0

  .searchdiv
    height: 100%
    width: 80%

  .search-input
    display: block
    width: 100%
    height: 100%
    padding-left: 50px
    font-size: 1.2rem
    border: $secondary 2px solid
    color: $grey
    font-weight: bold

  .search-button
    background-color: $primary
    width: 180px
    font-weight: bold

  .cards
    max-width: 1200px
    min-height: 70vh
    margin: 0 auto
    display: flex
    flex-wrap: wrap
    justify-content: center
    align-items: flex-start
    margin-top: 10px
    padding-bottom: 100px

  .card
    width: 340px
    margin: 15px
    padding: 25px 25px 40px 25px
    border-radius: 25px
    background: white
    display: flex
    flex-direction: column

  .card-button
    color: $primary
    border: $primary 1.5px solid
    width: 250px
    padding: 15px 20px
    font-weight: bold

  .card-button:hover
    color: $secondary
    background-color: $primary

  .card-username
    margin-bottom: 5px

  .card-name
    margin-bottom: 15px
    font-size: 1.33rem

  .card-email
    color: $grey
    margin-bottom: 40px

  .card-location
    background-color: $secondary
    border-radius: 20px
    padding: 20px 45px 30px 45px
    margin-bottom: 30px
    position: relative

  .card-location--icon
    position: absolute
    left: 15px
    top: 20px

  .card-city
    font-weight: bold
    margin-bottom: 10px

  .card-street
    font-size: 0.8rem
    margin-bottom: 5px

  .card-address
    font-size: 0.8rem

  .card-website
    color: $primary
    align-self: center
    margin-bottom: 40px


</style>
