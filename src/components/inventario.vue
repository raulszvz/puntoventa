<template>
  <div class="inventario">
    <b-carousel :autoplay="false">
        <b-carousel-item v-for="(slide, i) in slides" :key="i">
            <section class="hero is-fullheight is-light">
                <div class='itemContainer'>
                    <!--<div class="itemTitle">
                        <h1 class="Title">Titulo</h1>
                    </div>-->
                    <div class="columns is-multiline">
                        <div class="column is-one-quarter" v-for="(items, j) in slide" :key="j">
                            <div class="card">
                                <div class="card-image" @click="isComponentModalActive = true">
                                    <figure class="image is-4by3">
                                        <img :src=items.image alt="Placeholder image">
                                    </figure>
                                </div>
                                <div class="card-content">
                                    <div class="content textFormat">
                                        <b>{{items.product}}</b><br>
                                        ${{items.price}}
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
            isComponentModalActive: false,
        }
    }
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
