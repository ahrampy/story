<template>
  <div id="app">
    <Nav />
    <router-view/>
  </div>
</template>

<script>
import Nav from './components/Nav'

export default {
  name: "App",
  components: {
    Nav
  }
}
</script>

<style lang="scss">
@import "./assets/reset";
@import "./assets/sass/variables";

#app {
  font-family: $mainFont;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $mainColor;
}

#nav {
  padding: 30px;
}

#nav a {
  color: $mainColor;
}

#nav a.router-link-exact-active {
  color: $activeColor;
}
</style>
