<template>
   <section>
     <div class="bgimg">
       <main>
         <div class="info">
           <div class="info-wrapper">
             <h1 class="info-title">Specializujeme se na vyvoj produktu</h1>
             <p class="info-desc">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quidem excepturi sunt sequi quia tempora consequuntur sit quis natus odit dolorum?</p>
             <button class="info-contact btncurve">KONTAKTUJE NAS --></button>
           </div>
         </div>
         <form @submit.prevent="log">
           <h2 class="form-subtitle">Prihlaste sa</h2>
           <input required class="form-input" type="email" placeholder="Váš email" v-model="email">
           <input required class="form-input" type="password" placeholder="Heslo" v-model="password">
           <div class="flex">
             <div class="input-checkbox" @click.stop="hasAccepted = !hasAccepted">
               <span :class="{hide:!hasAccepted}" class="input-checkbox__accepted"></span>
             </div>
             <p class="form-rights">súhlasím so správou spracovaním a uchovaním mojich osobných údajov</p>
           </div>
           <button class="form-button btncurve">PRIHLASIT SA --></button>
         </form>
       </main>
     </div>
     <div class="lower">
       <div class="sponsors">
         <img src="~/assets/img/ceskatelevize.jpg" alt="" class="sponsor">
         <img src="~/assets/img/ceskatelevize.jpg" alt="" class="sponsor">
         <img src="~/assets/img/ceskatelevize.jpg" alt="" class="sponsor">
         <img src="~/assets/img/ceskatelevize.jpg" alt="" class="sponsor">
         <img src="~/assets/img/ceskatelevize.jpg" alt="" class="sponsor">
       </div>
       <div class="lower-photodiv">
         <img src="~/assets/img/laptop.png" alt="" class="laptop">
         <p class="lowet-getknow">POZNEJTE PIXELMATE TEAM</p>
         <h2 class="lower-title">Jsme mladi a hravi, startupy nas bavi</h2>
       </div>
       <div class="lower-div">
         <p class="lower-div__parag">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Cupiditate, perspiciatis quos! Eos aut rem maxime necessitatibus asperiores hic fugiat aliquid! Doloribus quae temporibus illo. At reiciendis, dignissimos dolorem perspiciatis nisi veniam ipsam consequatur, iusto eius amet ipsa minima quibusdam, nemo nesciunt porro aperiam aliquid autem esse? Ipsa beatae exercitationem cupiditate.</p>
         <p class="lower-div__parag">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Cupiditate, perspiciatis quos! Eos aut rem maxime necessitatibus asperiores hic fugiat aliquid! Doloribus quae temporibus illo. At reiciendis, dignissimos dolorem perspiciatis nisi veniam ipsam consequatur</p>
       </div>
       <NuxtLink to="/designers">
         <button class="lower-button btncurve">CO DALSIHO SE SUSKA --></button>
       </NuxtLink>
     </div>
   </section>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  data() {
    return {
      email: '' as string,
      password: '' as string,
      isAccepted: false as boolean,
      hasAccepted: false as boolean,
    }
  },
  methods: {
    log() : void {
      if(this.hasAccepted) {
        console.log(this.email,this.password)
        this.email = ''
        this.password = ''
        this.hasAccepted = false
      }
    }
  }
})
</script>

<style lang="sass" scoped>
    .bgimg
      background: url(~/assets/img/background.png) , linear-gradient(rgba(0,0,0,0.9),rgba(0,0,0,0.9))
      height: 100vh
      background-size: cover

    main
      width: 100%
      max-width: 1640px
      margin: 0px auto
      padding-top: 200px
      display: flex

    .info
      width: 65%

    .info-wrapper
      max-width: 800px
      margin: 0px auto
      width: 90%

    .info-title
      font-size: 4rem
      line-height: 1.33
      color: white
      margin-bottom: 30px

    .info-desc
      color: $grey
      font-weight: bold
      line-height: 1.75
      max-width: 650px
      margin-bottom: 35px

    .info-contact
      background-color: $primary
      color: $secondary
      width: 240px
      padding: 17px 0px
      font-weight: bold


    form
      width: 100%
      max-width: 420px
      background: white
      border-radius: 5px
      padding: 30px 30px 45px 30px
      display: flex
      flex-direction: column
      align-items: flex-start
      margin: 0px 15px

    .form-subtitle
      margin-bottom: 25px
      font-weight: 900

    .form-input
      width: 100%
      margin-bottom: 20px
      padding: 15px

    .input-checkbox
      width: 25px
      height: 25px
      border-radius: 50%
      border: 1.5px solid #0f33ff
      margin-right: 10px
      cursor: pointer
      display: flex
      justify-content: center
      align-items: center

    .input-checkbox__accepted
      width: 15px
      height: 15px
      border-radius: 50%
      background-color: $primary

    .form-rights
      color: grey
      font-size: 0.9rem
      line-height: 1.5
      width: 80%

    .form-button
      margin-top: 35px
      margin-left: 0px
      background: #0f33ff
      width: 100%
      padding: 20px 0px
      font-weight: bold
      font-size: 1rem

    .lower
        max-width: 1640px
        margin: 0px auto
        padding: 0px 20px

    .lower-photodiv
      position: relative
      max-width: 1320px
      margin: 0px auto

    .sponsors
      display: flex
      justify-content: space-around
      transform: translateY(-50%)
      background: white
      padding: 20px 0px
      box-shadow: 1px 1px 16px 3px rgba(0,0,0,0.15)
      margin-bottom: 150px

    .sponsor
        width: 170px
        filter: grayscale(100%)

    .lowet-getknow
      color: $primary
      margin-bottom: 20px
      font-weight: bold

    .lower-title
      font-size: 3rem
      max-width: 500px
      line-height: 1.33
      margin-bottom: 60px

    .lower-div
      display: flex
      justify-content: space-between
      max-width: 1320px
      padding: 0px 10px
      margin: 0px auto

    .lower-div__parag
      width: 100%
      max-width: 650px
      padding-right: 45px
      line-height: 1.66

    .lower-button
      background-color: $primary
      display: block
      margin: 0px auto
      margin-top: 50px
      margin-bottom: 100px
      width: 250px
      padding: 20px 0px
      font-weight: bold
      color: $secondary
      border: 2px solid $primary

    .lower-button:hover
      background-color: $secondary
      color: $primary

    .laptop
      position: absolute
      width: 590px
      right: 5%
      top: -75%
      z-index: -2

    @media (max-width: 1000px)
      .sponsor
        width: 90px
      .info-title
        font-size: 2.25rem
        max-width: 400px
      .info-desc
        font-size: 0.75rem
        max-width: 300px
      .laptop
        width: 390px
        top: 25%




    @media (max-width: 600px)
      main
        flex-direction: column
        padding-top: 120px
        display: flex
      .info-title
        font-size: 1.75rem
        max-width: 600px
        text-align: center
      .info-desc
        font-size: 0.66rem
        max-width: 600px
        text-align: center
      .info
        width: 100%
      .info-contact
        width: 170px
        padding: 13px 0px
        font-weight: bold
        font-size: 0.8rem
        margin: 0px auto
        display: block
        margin-bottom: 55px
      form
        padding: 10px
        margin: 0px
        max-width: 600px
      .form-subtitle
        margin-bottom: 15px
        font-weight: 900
        font-size: 1rem
      .form-input
        width: 100%
        margin-bottom: 20px
        padding: 10px
        margin-bottom: 10px
      .form-button
        margin-top: 15px
        margin-left: 0px
        font-size: 0.66rem
        padding: 10px 0px
        font-size: 1rem
      .sponsors
        max-width: 600px
        justify-content: center
      .sponsor
        width: 40px
        flex: 1
      .lower-div
        align-items: center
        flex-direction: column
      .lower-div__parag
        padding-right: 0px
        line-height: 1.66
        margin-bottom: 40px
      .laptop
        width: 350px
        top: 10%
        right: -20%
      .lower-title
        font-size: 2rem
        margin-bottom: 80px


</style>
