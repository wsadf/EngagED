<template>
  <div id="app">
    <!-- <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav> -->
    <router-view />
  </div>
</template>

<style lang="scss">
@import '~@/assets/scss/main.scss';

html,
body {
  font-family: $body-font-family;
}

#app {
  font-family: $body-font-family;
}
</style>