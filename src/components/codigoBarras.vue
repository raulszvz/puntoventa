<template>
  <div class="codigoBarras">
     <div class="containerCodigoBarras">
       <div class="box">
        <article class="media" v-for="(producto, i) in productos" :key="i">
          <div class="media-left">
            <strong>{{producto.modelo}}</strong>
          </div>
          <div class="media-content">
            <div class="content">
              <!--figure class="image">
                <img src="https://s3-eu-west-1.amazonaws.com/js-barcode/barcodes/init.svg" alt="Image">
              </figure>-->
              <barcode v-bind:value=producto.id>
                Show this if the rendering fails.
              </barcode>
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
import VueBarcode from 'vue-barcode';
const axios = require('axios');

export default {
  name: 'codigoBarras',
  components: {
    'barcode': VueBarcode
  },
  props: {

  },
  data(){
        return {
            producto: [
                {id:"12345", img:'https://bulma.io/images/placeholders/1280x960.png', producto:'Producto 1', precio:'23.50'},
                {id:"12346", img:'https://bulma.io/images/placeholders/1280x960.png', producto:'Producto 2', precio:'37.50'},
                {id:"12347", img:'https://bulma.io/images/placeholders/1280x960.png', producto:'Producto 3', precio:'41.00'},
            ],
            productos: []
        }
  },
  created(){
        this.readDoc();
    },
    methods:{
        async readDoc() {
            try {
                let response = await axios.get('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/read/producto');
                this.productos = response.data;
                console.log(this.productos);
            } catch (error) {
                console.error(error);
            }
        },
    },
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