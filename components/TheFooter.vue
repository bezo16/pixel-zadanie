<template>
  <footer>
       <p>all rights reserved 2013- Pixelmate s.r.o</p>
       <img src="~/assets/img/whitelogo.svg" alt="pixelmate footer logo">
       <p class="right">zasady ochrany udajov</p>
  </footer>
</template>

<style lang="sass" scoped>
  footer
    display: flex
    align-items: center
    background-color: #151331
    height: 120px
    padding: 0px 50px

  p
    color: grey
    flex: 1

  img
    width: 170px

  @media (max-width: 1000px)
    p
      font-size: 0.5rem
    footer
      padding: 0px 10px

</style>
