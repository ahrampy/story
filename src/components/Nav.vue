<template>
  <div class="nav">
    <h1>Nav</h1>
    <div id="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </div>
</template>

<script>
export default {

};
</script>

<style scoped>
.nav {
  display: flex;
  justify-content: flex-end;
  background: darkgrey;
  height: 50px;
  padding: 5px;
}
</style>