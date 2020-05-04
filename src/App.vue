<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <div class="columns is-gapless">
      <div class="column is-two-thirds">
        <inventario/>
      </div>
      <div class="column is-one-third">
        <cobrar/>
      </div>
    </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import inventario from './components/inventario.vue'
import cobrar from './components/cobrar.vue'

export default {
  name: 'App',
  components: {
    inventario,
    cobrar
  }
}
</script>

<style>
/*#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}*/
</style>
