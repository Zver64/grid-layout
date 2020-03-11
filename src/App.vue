<template>
  <div id="app">
    <div id="nav"></div>
    <router-view />
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Montserrat&display=swap');
html {
  box-sizing: border-box;
  background-color: var(--grey);
  font-family: 'Montserrat', sans-serif;
  width: 100%;
}
* {
  box-sizing: inherit;
}
#app {
  max-width: 100vw;
  width: 1200px;
  padding: 0 15px;
  margin: 0 auto;
}
</style>
