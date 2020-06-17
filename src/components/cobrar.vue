<template>
  <div class="cobrar">
    <navCobrar/>
    <div class="articulosVenta">
      <div class="box" v-for="(venta, i) in ventas" :key="i">
        <article class="media">
          <div class="media-left">
            <figure class="image is-64x64">
              <img src="https://bulma.io/images/placeholders/128x128.png" alt="Image">
            </figure>
          </div>
          <div class="media-content">
            <div class="content">
              <p>
                <strong>{{venta.producto}}</strong><br>
                <b-icon icon="cash-usd-outline"></b-icon>{{venta.precio}}<br>
                <b-switch>Apartar</b-switch><br>
              </p>
            </div>
            <nav class="level is-mobile">
              <div class="level-left">
                <a class="level-item" aria-label="retweet">
                  <b-numberinput size="is-small" min="1"></b-numberinput>
                </a>
                <a class="level-item" aria-label="like">
                  <b-icon icon="delete"></b-icon>
                </a>
              </div>
            </nav>
          </div>
        </article>
      </div>
    </div>
    <div class="importe">
      <div class="box">
        <article class="media">
          <div class="media-left">
            <strong>Total</strong>
          </div>
          <div class="media-content">
            <div class="content">
            $100.67
            </div>
            <nav class="level is-mobile">
              <b-button type="is-primary" expanded outlined>Efectivo</b-button><br>
              <b-button type="is-primary" expanded>Tarjeta</b-button>          
            </nav>
          </div>
        </article>
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
