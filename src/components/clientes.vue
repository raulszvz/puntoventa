<template>
  <div class="clientes">
    <div class="containerClientes">
      <div class="box">
        <article class="media" v-for="(cliente, i) in clientes" :key="i">
          <div class="media-left">
            <figure class="image is-64x64">
              <img src="https://bulma.io/images/placeholders/128x128.png" alt="Image">
            </figure>
          </div>
          <div class="media-content">
            <div class="content">
              <p>
                <strong>{{cliente.nombre}}</strong><br>
                <b-icon icon="card-account-details"></b-icon> {{cliente.id}}<br>
                <b-icon icon="email"></b-icon> {{cliente.email}}<br>
                <b-icon icon="star"></b-icon> {{cliente.puntos}}<br>
              </p>
            </div>
            <nav class="level is-mobile">
              <div class="level-left">
                <a class="level-item" aria-label="retweet">
                  <b-icon icon="pencil"></b-icon>
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
  </div>
</template>

<script>
export default {
  name: 'clientes',
  props: {

  },
  data(){
        return {
            clientes: [
                {id:12345, nombre:"John Smith", email:"john@email.com", puntos:50, img: ""},
                {id:12346, nombre:"Jane Cox", email:"jane@email.com", puntos:40, img: ""},
                {id:12347, nombre:"Adam Levine", email:"adam@email.com", puntos:70, img: ""},
            ],
        }
  }
}
</script>

<style>
    .containerClientes{
        background-color: #FFF;
        border-radius: 20px;
        width: 500px;
        height: 500px;
    }
</style>