<template>
  <section class="topbar">

    <transition name="fade">
      <div class="modal" v-if="showLogin" @click.self="toggleLogin" >
        <div class="modal-wrapper">
          <div @click.self="toggleLogin" class="modal-close">x</div>
          <h2 class="modal-subtitle">Prihlasit sa</h2>
          <p class="modal-desc">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cum nesciunt natus beatae ducim</p>
          <form @submit.prevent="login" class="modal-form">
            <input class="modal-input" type="email" placeholder="Váš email" required v-model="email">
            <button class="modal-button">ODESLAT</button>
          </form>
        </div>
      </div>
    </transition>

    <div class="topbar-wrp">
      <img v-if="isHomepage" class="logo" src="~/assets/img/whitelogo.svg" alt="">
      <img v-else class="logo" src="~/assets/img/blacklogo.svg" alt="">
      <img class="hamburger" src="~/assets/img/whitehamburger.svg" @click.self="toggleMobileMenu" alt="hambuger menu icon, used for opening navbars on mobile phones">
      <ul class="list">
        <li>
          <NuxtLink to="/designers">
            <button class="nav-button" :class="{greybtn:!isHomepage}">Designeri</button>
          </NuxtLink>
        </li>
        <li>
          <button class="nav-button" :class="{greybtn:!isHomepage}">Portfolio</button>
        </li>
        <li>
          <button class="nav-button primarybtn" :class="{'greybtn-primary':!isHomepage}" @click.self="toggleLogin">Prihlasit sa</button>
        </li>
      </ul>
    </div>

    <transition name="mobilenav">
      <div class="mobilenav" v-if="showMobileNav">
        <nav>
          <NuxtLink to="/designers">
            <button @click="toggleMobileMenu" class="mobilenav-link">Designeri</button>
          </NuxtLink>
          <button @click="toggleMobileMenu" class="mobilenav-link">Portfolio</button>
          <button @click="toggleMobileMenu" class="mobilenav-link">Prihlasit sa</button>
        </nav>
      </div>
    </transition>

  </section>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      showLogin: false as boolean,
      showMobileNav: false as boolean,
      email: '' as string,
    }
  },
  computed: {
    isHomepage() : boolean {
      return this.$route.path === '/' ? true : false
    }
  },
  methods: {
    toggleLogin() : void {
      this.showLogin = !this.showLogin
    },
    login() {
      this.email = ''
      this.toggleLogin()
    },
    toggleMobileMenu() {
      this.showMobileNav = !this.showMobileNav
    }
  },
  mounted() : void {
    addEventListener('keydown',(e) => {
      if(e.code === 'Escape' && this.showLogin) console.log('toglujem')
      if(e.code === 'Escape' && this.showLogin) this.toggleLogin()
      })
  }
})
</script>

<style scoped lang="sass">
  .topbar
    height: 70px
    display: flex
    align-items: flex-end
    justify-content: center
    position: fixed
    top: 0px
    left: 0px
    width: 100%
    padding: 0px 20px

  .topbar-wrp
    width: 90%
    display: flex
    align-items: center

  .logo
    width: 11.5rem

  .list
    margin-left: auto
    display: flex

  .hamburger
    display: none
    margin-left: auto
    margin-right: 10px
    cursor: pointer

  .nav-button
    font-weight: bold
    padding: 10px 32px

  .primarybtn
    border: 1.5px solid $secondary
    border-top-right-radius: 30px
    border-bottom-right-radius: 30px
    border-top-left-radius: 30px

  .primarybtn:hover
    background: $secondary
    color: $primary

  .greybtn
    color: #8E929F

  .greybtn-primary
    width: 180px
    color: #8E929F
    border: #8E929F 2px solid
    border-top-right-radius: 30px
    border-bottom-right-radius: 30px
    border-top-left-radius: 30px
    margin-left: 30px

  .greybtn-primary:hover
    color: white
    background-color: #8E929F

  .modal
    position: fixed
    top: 0px
    left: 0px
    height: 100vh
    width: 100%
    background: rgba(0,0,0,0.75)
    display: flex
    justify-content: center
    align-items: center
    z-index: 5

  .modal-wrapper
    background-color: white
    max-width: 500px
    padding: 25px
    padding-bottom: 40px
    border-radius: 5px
    position: relative

  .modal-subtitle
    color: black
    font-size: 1.25rem
    text-align: center
    margin-bottom: 20px

  .modal-desc
    font-size: 0.85rem
    line-height: 1.75
    margin: 0px auto
    margin-bottom: 30px
    width: 90%
    text-align: center

  .modal-close
    position: absolute
    right: 15px
    top: 15px
    width: 27px
    height: 27px
    line-height: 23px
    border-radius: 50%
    background-color: #ecefff
    color: #1639ff
    text-align: center
    cursor: pointer
    font-weight: bold

  .modal-close:hover
    background-color: #1639ff
    color: #ecefff

  .modal-form
    display: flex
    flex-direction: column
    align-items: center

  .modal-input
    padding: 15px 30px 15px 10px
    font-weight: bold
    font-size: 0.65rem
    width: 220px
    color: $grey
    border: $secondary 2px solid

  .modal-button
    background-color: $primary
    color: $secondary
    font-weight: bold
    margin-top: 25px
    width: 150px
    padding: 15px 15px
    border-top-right-radius: 30px
    border-bottom-right-radius: 30px
    border-top-left-radius: 30px
    font-size: 0.75rem

  .mobilenav
    position: absolute
    left: 0px
    top: calc(100% + 15px)
    width: 100%
    height: 150px
    background-color: white
    display: flex
    justify-content: center
    align-items: center
    box-shadow: 1px 1px 16px 4px rgba(0,0,0,0.15)

  .mobilenav-link
    color: $grey
    border: 1.5px solid $primary
    padding: 10px 25px
    border-radius: 50px
    font-weight: bold

  .mobilenav-link:hover
    color: $secondary
    background-color: $primary



  @media (max-width: 1000px)
    .list
      display: none
    .hamburger
      display: initial


</style>


