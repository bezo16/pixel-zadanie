<template>
  <section class="topbar">
    <div class="modal" v-if="showLogin" @click.self="toggleLogin" >
      <div class="modal-wrapper">
        <div @click.self="toggleLogin" class="modal-close">x</div>
        <h2 class="modal-subtitle">Prihlasit sa</h2>
        <p class="modal-desc">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cum nesciunt natus beatae ducim</p>
        <form @submit.prevent="login" class="modal-form">
          <input class="modal-input" type="text" placeholder="Váš email" required v-model="email">
          <button class="modal-button">ODESLAT</button>
        </form>
      </div>
    </div>
    <div class="topbar-wrp">
      <img class="logo" src="~/assets/img/logo.svg" alt="pixelmate brand logo">
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
            <button class="nav-button" :class="{'greybtn-primary':!isHomepage}" @click.self="toggleLogin">Prihlasit sa</button>
          </li>
        </ul>
    </div>
  </section>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      showLogin: false as boolean,
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
      console.log(this.email)
      this.email = ''
      this.toggleLogin()
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
    height: 10rem
    display: flex
    align-items: center
    justify-content: center
    position: fixed
    top: 0px
    left: 0px
    width: 100%
    padding: 0px 50px

  .topbar-wrp
    width: 90%
    display: flex
    align-items: center

  .logo
    width: 11.5rem

  .list
    margin-left: auto
    display: flex

  .nav-button
    font-weight: bold
    padding: 10px 30px

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


</style>


