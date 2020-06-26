<template>
  <div class="cobrar">
    <navCobrar/>
    <div class="articulosVenta">
      <div class="card" v-for="(venta, i) in ventas" :key="i">
        <div class="card-content">
          <div class="media">
            <div class="media-left">
              <figure class="image is-64x64">
                <img src="https://bulma.io/images/placeholders/128x128.png" alt="Image">
              </figure>
            </div>
            <div class="media-content">
               <strong>{{venta.producto}}</strong><br>
                <b-icon icon="cash-usd-outline"></b-icon>{{venta.precio}}<br>
                <b-switch>Apartar</b-switch><br> 
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="importe">
      <div class="card">
        <div class="card-content">
          <div class="media">
            <div class="media-left">
              <strong>Importe</strong><br>
            </div>
            <div class="media-content">
                <h1>Subtotal:</h1>
                <h1>Total:</h1>
                <button class="button is-primary">Pagar</button>
            </div>
          </div>
        </div>
      </div>
    </div>
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

  },
  data(){
        return {
            ventas: [
                {img:'https://bulma.io/images/placeholders/1280x960.png', producto:'Producto 1', precio:'23.50'},
                {img:'https://bulma.io/images/placeholders/1280x960.png', producto:'Producto 2', precio:'37.50'},
                {img:'https://bulma.io/images/placeholders/1280x960.png', producto:'Producto 3', precio:'41.00'},
            ],
        }
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
    .box{
      margin-bottom: 0px;
    }
</style>
