<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss">
@import "./assets/icon.css";
@import "./assets/global.scss";
*{
  padding: 0;
  margin: 0;
}
@media screen and (min-width: 1024px) {
  html {
    font-size: $font-large;
  }
}
@media screen and (min-width: 769px) and (max-width: 1023px) {
  html {
    font-size: $font-normal;
  }
}
@media screen and (min-width: 381px) and (max-width: 768px) {
  html {
    font-size: $font-mid;
  }
}
@media screen and (max-width: 380px) {
  html {
    font-size: $font-small;
  }
}
</style>
