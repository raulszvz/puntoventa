<template>
  <div class="inventario">
    <b-carousel :autoplay="false">
        <b-carousel-item v-for="(carousel, i) in carousels" :key="i">
            <section :class="`hero is-fullheight is-light`">
                <!--<div class="hero-body has-text-centered">
                    <h1 class="title">{{carousel.text}}</h1>
                </div>-->
                <div class='itemContainer'>
                    <div class="columns is-multiline">
                        <div class="column is-one-quarter" v-for="(inventario, i) in inventario" :key="i">
                            <div class="card">
                                <div class="card-image">
                                    <figure class="image is-4by3">
                                        <img src="'${inventario.image}'" alt="Placeholder image">
                                    </figure>
                                </div>
                                <div class="card-content">
                                    <div class="content">
                                        {{inventario.text}}
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
        </b-carousel-item>
    </b-carousel>
  </div>
</template>

<script>
export default {
  name: 'inventario',
  data(){
        return {
            carousels: [
                { text: 'Slide 1', color: 'primary' },
                { text: 'Slide 2', color: 'info' },
                { text: 'Slide 3', color: 'success' },
                { text: 'Slide 4', color: 'warning' },
                { text: 'Slide 5', color: 'danger' }
            ],
            inventario: [
                { image: 'https://bulma.io/images/placeholders/1280x960.png', text: 'Producto 1' },
                { image: 'https://bulma.io/images/placeholders/1280x960.png', text: 'Producto 2' },
                { image: 'https://bulma.io/images/placeholders/1280x960.png', text: 'Producto 3' },
                { image: 'https://bulma.io/images/placeholders/1280x960.png', text: 'Producto 4' },
                { image: 'https://bulma.io/images/placeholders/1280x960.png', text: 'Producto 5' }
            ]
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
    .itemContainer{
        padding: 5%;
      /*justify-content: center;
      align-items: center;*/

    }
</style>
