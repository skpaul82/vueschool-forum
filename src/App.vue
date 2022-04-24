<template>
  <!-- <router-link :to="{ name: 'Home' }">
    <img alt="Vue logo" src="./assets/logo.png" />
  </router-link> -->
  <div class="container">
    <router-view/>
  </div>
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>
@import "assets/style.css";
@import "~bootstrap/dist/css/bootstrap.css";
/* @import "~fontawesome/css/fontawesome.css" */
</style>
