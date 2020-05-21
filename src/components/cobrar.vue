<template>
  <div class="cobrar">
    <navCobrar/>
  </div>
</template>

<script>
import navCobrar from './../components/navCobrar.vue'

export default {
  name: 'cobrar',
  components: {
    navCobrar
  },
  props: {

  }
}
</script>

<style>
    .cobrar {
        background-color: #FFFFFF;
        height: 100vh;
        padding: 0;
        margin: 0;
    }
</style>
