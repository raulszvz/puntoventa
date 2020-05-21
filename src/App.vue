<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <div class="columns is-gapless">
      <div class="column is-two-thirds">
        <navInventario/>
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
import navInventario from './components/navInventario.vue'

export default {
  name: 'App',
  components: {
    inventario,
    cobrar,
    navInventario,
  }
}
</script>

<style>

</style>
