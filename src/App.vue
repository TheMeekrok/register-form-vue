<template>
  <div class="wrapper">
    <Register/>
  </div>
</template>

<script>
import Register from './components/RegisterForm.vue'

export default {
  name: 'App',
  components: {
    Register
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
}
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 70vw;
  height: 100vh;
  margin: auto;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
