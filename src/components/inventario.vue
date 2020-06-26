<template>
  <div class="inventario">
            <section class="hero is-fullheight is-light">
                <div class='itemContainer'>
                    <div class="columns is-multiline">
                        <div class="column is-one-quarter" v-for="(item, j) in productos" :key="j">
                            <div class="card">
                                <div class="card-image" @click="isComponentModalActive = true">
                                    <figure class="image is-4by3">
                                        <img :src=item.imgURL alt="Placeholder image">
                                    </figure>
                                </div>
                                <div class="card-content">
                                    <div class="content textFormat">
                                        <b>{{item.modelo}}</b><br>
                                        ${{item.precio}}
                                    </div>
                                    <button class="button is-primary" @click="verificarCarrito">Agregar</button>
                                </div>
                            </div>
                            <b-modal :active.sync="isComponentModalActive"
                                trap-focus
                                :destroy-on-hide="false"
                                aria-role="dialog"
                                aria-modal>
                                <detallesProducto :producto='item'/>
                            </b-modal>
                        </div>
                    </div>
                </div>
            </section>
  </div>
</template>

<script>
import detallesProducto from './../components/detallesProducto.vue'
const axios = require('axios');

export default {
  name: 'inventario',
  components: {
    detallesProducto
  },
  data(){
        return {
            id: 'ABC', 
            productos: [],
            compras: [],
            contador: 0,
            isComponentModalActive: false,
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
        async verificarCarrito() {
            try {
                let response = await axios.get('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/read/carrito/'+this.id);
                let onlyData = response.data;
                console.log(response.data);
                if(onlyData.id == this.id){
                    console.log('si');
                    this.contador = onlyData.length
                    this.agregarCarrito();
                }else{
                    console.log('no');
                    this.iniciarCarrito();
                }
            } catch (error) {
                console.error(error);
            }
        },
        async iniciarCarrito() {
                axios.post('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/create/carrito', {
                    id: this.id,
                })
                .then(function (response) {
                    console.log(response);
                })
                .catch(function (error) {
                    console.log(error);
                });
        },
        async agregarCarrito() {
                //let articuloNum = toString('articulo'+this.contador);
                axios.put('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/update/carrito/'+this.id,{
                    articuloNum:'cosa'
                })
                .then(function (response) {
                    console.log(response);
                })
                .catch(function (error) {
                    console.log(error);
                });
        },
    },  
}
</script>

<style>
    .inventario {
        background-color: #D3D3D3;
        display: flex;
        flex-direction: column;
        height:100vh;
        padding: 0;
        margin: 0;
    }
    .itemTitle{
        padding: 1%;
    }
    .itemContainer{
        padding: 5%;
    }
    .textFormat{
        text-align: center;
    }
    .detallesProducto{
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>
