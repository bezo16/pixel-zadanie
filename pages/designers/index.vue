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
          <button class="card-button">ZOBRAZIT PROFIL --></button>
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
    min-height: 70vh
    margin: 0 auto
    display: flex
    flex-wrap: wrap
    justify-content: center
    margin-top: 100px
    padding-bottom: 100px

  .card
    width: 330px
    margin: 15px
    padding: 25px 25px 50px 25px
    border-radius: 25px
    background: white
    display: flex
    flex-direction: column

  .card-button
    color: $primary
    border: $primary 1.5px solid
    border-top-right-radius: 30px
    border-bottom-right-radius: 30px
    border-top-left-radius: 30px
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
