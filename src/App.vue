<template>
  <div id="app">
    <Weather msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Weather from './components/Weather.vue'

export default {
  name: 'App',
  components: {
    Weather
  }
}
</script>

<style>
body{
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #6d9bb6;
}
#app {
  text-align: center;
  background-color: #282c34;
  min-height: 400px;
  height: 70vh;
  width: 50vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
  border-radius: 62px;
  background: linear-gradient(145deg, #628ca4, #75a6c3);
  box-shadow:  21px 21px 31px #597f95, 
               -21px -21px 31px #81b7d7;
}
</style>
