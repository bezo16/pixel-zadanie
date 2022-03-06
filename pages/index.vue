<template>
   <section>
     <div class="bgimg">
       <main>
         <div class="info">
           <div class="info-wrapper">
             <h1 class="info-title">Specializujeme se na vyvoj produktu</h1>
             <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quidem excepturi sunt sequi quia tempora consequuntur sit quis natus odit dolorum?</p>
             <button>KONTAKTUJE NAS</button>
           </div>
         </div>
         <form>
           <h2 class="form-subtitle">Prihlaste sa</h2>
           <input class="form-input" type="text" placeholder="Váš email">
           <input class="form-input" type="password" placeholder="Heslo">
           <div class="flex">
             <span class="input-checkbox"></span>
             <p class="form-rights">súhlasím so správou spracovaním a uchovaním mojich osobných údajov</p>
           </div>
           <button class="form-button">PRIHLASIT SA -></button>
         </form>
       </main>
     </div>
     <div class="lower">
       <div class="sponsors">
         <img src="" alt="sponzor">
         <img src="" alt="sponzor">
         <img src="" alt="sponzor">
         <img src="" alt="sponzor">
         <img src="" alt="sponzor">
       </div>
       <div class="lower-photodiv">
        <p>POZNEJTE PIXELMATE TEAM</p>
        <h2>Jsme mladi a hravi, startupy nas bavi</h2>
       </div>
       <div class="lower-div">
         <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Cupiditate, perspiciatis quos! Eos aut rem maxime necessitatibus asperiores hic fugiat aliquid! Doloribus quae temporibus illo. At reiciendis, dignissimos dolorem perspiciatis nisi veniam ipsam consequatur, iusto eius amet ipsa minima quibusdam, nemo nesciunt porro aperiam aliquid autem esse? Ipsa beatae exercitationem cupiditate.</p>
         <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Cupiditate, perspiciatis quos! Eos aut rem maxime necessitatibus asperiores hic fugiat aliquid! Doloribus quae temporibus illo. At reiciendis, dignissimos dolorem perspiciatis nisi veniam ipsam consequatur</p>
       </div>
     </div>
   </section>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage'
})
</script>

<style lang="sass">
  .bgimg
    background: url(https://placekitten.com/1700/900) , linear-gradient(rgba(0,0,0,0.9),rgba(0,0,0,0.9))
    height: 100vh
    background-size: 100% 100%

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
      font-size: 4.25rem
      line-height: 1.5
      color: white


    form
      width: 35%
      background: white
      border-radius: 5px
      padding: 30px 30px 45px 30px
      display: flex
      flex-direction: column
      align-items: flex-start

    .form-subtitle
      margin-bottom: 20px
      font-weight: 900

    .form-input
      width: 100%
      margin-bottom: 20px
      padding: 15px

    .input-checkbox
      width: 40px
      height: 25px
      border-radius: 50%
      border: 1.5px solid #0f33ff
      margin-right: 10px

    .form-rights
      color: grey
      font-size: 0.9rem
      line-height: 1.5

    .form-button
      margin-top: 30px
      margin-left: 0px
      background: #0f33ff
      width: 100%
      padding: 20px 0px
      border-top-left-radius: 30px
      border-top-right-radius: 30px
      border-bottom-right-radius: 30px
      font-weight: bold
      font-size: 1rem
</style>
