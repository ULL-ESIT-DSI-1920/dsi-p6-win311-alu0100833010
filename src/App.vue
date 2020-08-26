<template>
  <div id="app">
    <win311-icon name="msdos"></win311-icon>
    <win311-window type="cpanel"></win311-window><br>
    <win311-window type="apps"></win311-window>
  </div>
</template>

<script>
import Win311Window from './components/Win311Window.vue';
import Win311Icon from './components/Win311Icon.vue';

export default {
  name: 'App',
  components: {
    "win311-window": Win311Window,
    "win311-icon": Win311Icon
  }
};
</script>

<style>
body {
  background: #56aca9;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
