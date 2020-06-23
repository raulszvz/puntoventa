<template>
  <div class="detallesProducto">
     <div class="containerDetalles">
       <div class="box">
        <article class="media">
          <div class="media-left">
            <figure class="image is-64x64">
              <img :src=producto.imgURL alt="Image">
            </figure>
          </div>
          <div class="media-content">
            <div class="content">
              <p>
                <strong>{{producto.modelo}}</strong><br>
                <b-icon icon="barcode"></b-icon> {{producto.id}}<br>
                <b-icon icon="watermark"></b-icon> {{producto.marca}}<br>
                <b-icon icon="format-list-bulleted-type"></b-icon> {{producto.tipo}}<br>
                <b-icon icon="arrow-split-vertical"></b-icon> {{producto.talla}}<br>
                <b-icon icon="information-outline"></b-icon> {{producto.descripcion}}<br>
                <b-icon icon="cash-usd-outline"></b-icon> {{producto.precio}}<br>
                <b-icon icon="counter"></b-icon> {{producto.existencias}}<br>
              </p>
            </div>
            <nav class="level is-mobile">
              <!--<div class="level-left">
                <a class="level-item" aria-label="retweet">
                  <b-icon icon="pencil"></b-icon>
                </a>
                <a class="level-item" aria-label="like">
                  <b-icon icon="delete"></b-icon>
                </a>
              </div>-->
            </nav>
          </div>
        </article>
      </div>
     </div>
  </div>
</template>

<script>
export default {
  name: 'detallesPoducto',
  props: {

  },
  data(){
        return {
            producto: 
                { id: '123', modelo: 'Modelo A', marca: 'Marca C', tipo: 'Blazer', talla: 'S', descripcion: 'Prenda de vestir', precio: '100', existencias: '6', imgURL: 'https://bulma.io/images/placeholders/1280x960.png'}
        }
  }
}
</script>

<style>
    .containerDetalles{
        background-color: #FFF;
        border-radius: 20px;
        width: 500px;
        height: 300px;
    }
</style>