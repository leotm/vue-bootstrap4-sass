<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style lang="scss">
// default...
@import "~bootstrap/scss/bootstrap.scss";
// custom bootstrap...
// @import "~bootstrap/scss/_nav.scss";
// custom app...
#app {

}
</style>
