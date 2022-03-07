<template>
  <section class="designer">
    <main v-if="designer.name">
      <section class="info">
        <NuxtLink class="backbtn" to="/designers">&#60;-- ZPET</NuxtLink>
        <p class="designer-username">{{ designer.username }}</p>
        <h2 class="designer-name">{{ designer.name }}</h2>
        <p class="designer-email">{{ designer.email }}</p>
        <div class="location">
          <img src="~/assets/img/location.svg" alt="" class="card-location--icon">
          <p class="designer-city">{{ designer.address.city }}</p>
          <p class="designer-street">{{ designer.address.street }} {{ designer.address.suite }}</p>
          <p class="designer-address">{{ designer.address.zipcode }} - {{ designer.address.city }}</p>
        </div>
        <p class="designer-website">{{ designer.website }}</p>
        <div class="moto">
          <h2 class="moto-subtitle">{{ designer.company.name }}</h2>
          <p class="moto-desc">{{ designer.company.catchPhrase }}</p>
        </div>
      </section>
      <section class="photo">
        <img class="developerimg" src="~/assets/img/developer.png" alt="programmer">
      </section>
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
    min-height: 100vh

  .backbtn
    color: $primary
    background-color: $secondary
    padding: 12px 25px
    display: block
    border-radius: 50px
    font-size: 0.9rem
    font-weight: bold
    margin-bottom: 35px
    align-self: flex-start

  main
    width: 100%
    min-height: calc(100vh - 10rem - 200px)
    max-width: 1640px
    margin: 0px auto
    padding-top: 50px
    display: flex
    justify-content: center

  .info
    width: 100%
    max-width: 400px
    display: flex
    flex-direction: column
    padding-bottom: 100px
    margin-left: 150px

  .designer-username
    margin-bottom: 5px

  .designer-name
    margin-bottom: 10px
    font-size: 1.75rem

  .designer-email
    margin-bottom: 30px
    font-size: 1.25rem

  .location
    background-color: $secondary
    border-radius: 20px
    padding: 20px 45px 30px 45px
    margin-bottom: 30px
    position: relative

  .card-location--icon
    position: absolute
    left: 15px
    top: 20px

  .designer-website
    color: $primary
    align-self: center
    margin-bottom: 40px
    text-decoration: underline
    font-size: 1.1rem
    font-weight: bold
    letter-spacing: 0.5px

  .moto
    box-shadow: -2px 2px 17px 1px rgba(0,0,0,0.1)
    padding: 30px 25px
    border-radius: 20px

  .designer-city
    font-weight: bold
    margin-bottom: 10px

  .designer-street
    font-size: 0.8rem
    margin-bottom: 5px

  .designer-address
    font-size: 0.8rem

  .developerimg
    width: 550px

  .moto-subtitle
    font-size: 1rem
    margin-bottom: 10px

  .moto-desc
    line-height: 1.5

  @media (max-width: 1000px)
    main
      flex-direction: column
      align-items: center
    .developerimg
      margin-bottom: 100px
    .info
      align-items: center
      margin-left: 0px
      padding-bottom: 40px

</style>
