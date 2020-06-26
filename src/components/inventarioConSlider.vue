<template>
  <div class="inventario">
    <b-carousel :autoplay="false">
        <b-carousel-item v-for="(producto, i) in productos" :key="i">
            <section class="hero is-fullheight is-light">
                <div class='itemContainer'>
                    <div class="itemTitle">
                        <strong class="Title">{{producto[0][0].tipo}}</strong>
                    </div>
                    <div class="columns is-multiline">
                        <div class="column is-one-quarter" v-for="(items, j) in producto" :key="j">
                            <div class="card">
                                <div class="card-image" @click="isComponentModalActive = true">
                                    <figure class="image is-4by3">
                                        <img :src=items.imgURL alt="Placeholder image">
                                    </figure>
                                </div>
                                <div class="card-content">
                                    <div class="content textFormat">
                                        <b>{{items.modelo}}</b><br>
                                        ${{items.precio}}
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <b-modal :active.sync="isComponentModalActive"
                    trap-focus
                    :destroy-on-hide="false"
                    aria-role="dialog"
                    aria-modal>
                    <detallesProducto/>
                </b-modal>
            </section>
        </b-carousel-item>
    </b-carousel>
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
            slides: [
                [
                    { image: 'https://bulma.io/images/placeholders/1280x960.png', product: 'Producto 1', price: '23.50' },
                    { image: 'https://bulma.io/images/placeholders/1280x960.png', product: 'Producto 2', price: '23.50' },
                    { image: 'https://bulma.io/images/placeholders/1280x960.png', product: 'Producto 3', price: '23.50' }
                ],
                [
                    { image: 'https://bulma.io/images/placeholders/1280x960.png', product: 'Producto 4', price: '23.50' },
                    { image: 'https://bulma.io/images/placeholders/1280x960.png', product: 'Producto 5', price: '23.50' }
                ]
            ],
            productos: [],
            productosAux: [],
            isComponentModalActive: false,
        }
    },
    created(){
        this.readDoc();
        this.sortProducts();
    },
    methods:{
        async readDoc() {
            try {
                let response = await axios.get('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/read/producto');
                let aux = []
                aux.push(response.data);
                console.log(aux);
                let productosVec = [[],[],[],[],[],[],[],[],[],[],[],[],[],[],[],[]];
                for(let i=0; i<this.aux.length; i++){
                    switch (this.aux[i].tipo) {
                        case 'Tops':
                            productosVec[0].push(this.aux[i]);
                            break;
                        case 'Camisas y blusas':
                            productosVec[1].push(this.aux[i]);
                            break;
                        case 'Ropa para dormir':
                            productosVec[2].push(this.aux[i]);
                            break;
                        case 'Lencería':
                            productosVec[3].push(this.aux[i]);
                            break;
                        case 'Básicos':
                            productosVec[4].push(this.aux[i]);
                            break;
                        case 'Trajes de baño':
                            productosVec[5].push(this.aux[i]);
                            break;
                        case 'Pantalones':
                            productosVec[6].push(this.aux[i]);
                            break;
                        case 'Jeans':
                            productosVec[7].push(this.aux[i]);
                            break;
                        case 'Shorts':
                            productosVec[8].push(this.aux[i]);
                            break;
                        case 'Faldas':
                            productosVec[9].push(this.aux[i]);
                            break;
                        case 'Accesorios':
                            productosVec[10].push(this.aux[i]);
                            break;
                        case 'Blazers':
                            productosVec[11].push(this.aux[i]);
                            break;
                        case 'Suéteres':
                            productosVec[12].push(this.aux[i]);
                            break;
                        case 'Calcetines':
                            productosVec[13].push(this.aux[i]);
                            break;
                        case 'Chamarras y abrigos':
                            productosVec[14].push(this.aux[i]);
                            break;
                        case 'Sudaderas':
                            productosVec[15].push(this.aux[i]);
                    }
                }
                //this.productos.push(productosVec);
                console.log(productosVec);
            } catch (error) {
                console.error(error);
            }
        },
        sortProducts(){
            
        }
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
