<template>
  <div id="app">
    <h1 class="title">RPG Character Creator</h1>
    <h2 class="subtitle">created by Alston Chan</h2>
    <Builder />
  </div>
</template>

<script>
import Builder from './components/Builder.vue'

export default {
  name: 'App',
  components: {
    Builder
  }
}
</script>

<style>
@font-face { font-family: RetroComputer; src: url("./fonts/retro_computer.ttf"); } 

body {
  height: 100vh;
  overflow-x: hidden;
  background-image: url("./img/backgrounds/bg0.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: bottom;
}

.title {
  color: white;
  filter: drop-shadow(0 2px 2px black)
}

.subtitle {
  color: white;
  filter: drop-shadow(0 2px 2px black);
  font-size: 16px;
}

#app {
  font-family: RetroComputer, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
