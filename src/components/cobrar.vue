<template>
  <div class="cobrar">
    <navCobrar/>
    <div class="articulosVenta">
      <div class="card" v-for="(compra, i) in compras" :key="i" >
        <div class="card-content">
          <div class="media">
            <div class="media-left">
              <figure class="image is-64x64">
                <img src="https://bulma.io/images/placeholders/128x128.png" alt="Image">
              </figure>
            </div>
            <div class="media-content">
               <strong>{{compra.modelo}}</strong><br>
                <b-icon icon="cash-usd-outline"></b-icon> {{compra.precio}}<br>
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
                <h1>Subtotal: {{sub}}</h1>
                <h1>Total: {{tot}}</h1>
                <button class="button is-primary" @click="createDoc">Pagar</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import navCobrar from './../components/navCobrar.vue'
const axios = require('axios');
const shortid = require('shortid');

export default {
  name: 'cobrar',
  components: {
    navCobrar
  },
  props: {

  },
  data(){
        return {
            compras: [],
            idCarrito: '',
            sub: 0,
            tot: 0,
            venta: [],
        }
  },
  created(){
    this.readDoc();
  },
  methods:{
    async readDoc() {
            try {
                let response = await axios.get('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/read/carrito/ABC');
                this.compras = response.data;
                delete this.compras.id
                this.idCarrito = response.data.id;
                console.log(this.compras);
                this.subtotal();
            } catch (error) {
                console.error(error);
            }
        },
    subtotal(){
      let vecAux = Object.values(this.compras);
      for(let i=0; i<vecAux.length; i++){
        this.sub += parseFloat(vecAux[i].precio);
        console.log(this.sub);
      }
      this.total();
    },
    total(){
      this.tot = this.sub;
    },
    async createDoc(){
            axios.post('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/create/venta', {
            id: shortid.generate(), 
            articulos: this.compras,
            subtotal: this.sub,
            total: this.tot,
        })
        .then(function (response) {
            console.log(response);
        })
        .catch(function (error) {
            console.log(error);
        });
        this.letreroRespuesta();
    },
    letreroRespuesta(){
      this.$buefy.snackbar.open({
        message: 'Compra realizada',
        type: 'is-warning',
        position: 'is-top',
        actionText: 'OK',
        indefinite: true,
        onAction: () => {
          this.$buefy.toast.open({
            message: 'Action pressed',
            queue: false
          })
        }
      })
    },
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
