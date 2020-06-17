<template>
  <div class="codigoBarras">
     <div class="containerCodigoBarras">
       <div class="box">
        <article class="media" v-for="(producto, i) in productos" :key="i">
          <div class="media-left">
            <strong>{{producto.producto}}</strong>
          </div>
          <div class="media-content">
            <div class="content">
              <!--figure class="image">
                <img src="https://s3-eu-west-1.amazonaws.com/js-barcode/barcodes/init.svg" alt="Image">
              </figure>-->
              <svg id="barcode"></svg>
            </div>
            <nav class="level is-mobile">
              <div class="level-left">
                <a class="level-item" aria-label="retweet">
                  <b-button type="is-primary">Imprimir</b-button>
                </a>
                <a class="level-item" aria-label="like">
                  <b-button type="is-primary">Descargar</b-button>
                </a>
              </div>
            </nav>
          </div>
        </article>
      </div>
     </div>
  </div>
</template>

<script>
import jsbarcode from 'jsbarcode';
//import Canvas from 'canvas';

export default {
  name: 'codigoBarras',
  props: {

  },
  data(){
        return {
            productos: [
                {img:'https://bulma.io/images/placeholders/1280x960.png', producto:'Producto 1', precio:'23.50'},
                {img:'https://bulma.io/images/placeholders/1280x960.png', producto:'Producto 2', precio:'37.50'},
                {img:'https://bulma.io/images/placeholders/1280x960.png', producto:'Producto 3', precio:'41.00'},
            ],
        }
  },
  methods:{
    barcodeGenerate(){
      //var canvas = new Canvas();
      //jsbarcode(canvas, "Hello");
      jsbarcode("#barcode", "1234", {
        format: "pharmacode",
        lineColor: "#0aa",
        width: 4,
        height: 40,
        displayValue: false
      });
    }
  }
}
</script>

<style>
    .containerCodigoBarras{
        background-color: #FFF;
        border-radius: 20px;
        width: 500px;
        height: 500px;
    }
</style>