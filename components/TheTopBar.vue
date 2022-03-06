<template>
  <section class="topbar">
    <div class="topbar-wrp">
      <img class="logo" src="~/assets/img/logo.svg" alt="pixelmate brand logo">
        <ul class="list">
          <li>
            <NuxtLink to="/designers">
              <button class="nav-button">Designeri</button>
            </NuxtLink>
          </li>
          <li>
            <button class="nav-button">Portfolio</button>
          </li>
          <li>
            <button class="nav-button">Prihlasit sa</button>
          </li>
        </ul>
    </div>
  </section>
</template>

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
    cursor: pointer

</style>


