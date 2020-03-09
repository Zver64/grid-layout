<template>
  <div id="app">
    <div id="nav"></div>
    <router-view />
  </div>
</template>

<style lang="scss">
html {
  box-sizing: border-box;
  background-color: $c-background;
}
#app {
  max-width: 1200px;
  margin: 0 auto;
}
</style>
