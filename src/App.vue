<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
};
</script>

<style>
  html, body {
    height: 100vh;
  }
  body {
    background-color: #11111d;
    font-family: 'Roboto', sans-serif;
    margin: 0;
  }
  #app {
    height: 100%;
  }
</style>
