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
        <article class="media">
          <div class="media-content">
            <div class="content">
                <section class="subContainer">
            <strong>Agregar cliente</strong>
            <b-field>
                <b-input placeholder="Nombre" v-model="cliente.nombre"></b-input>
            </b-field>
            <b-field>
                <b-datepicker placeholder="Fecha de nacimiento" v-model="cliente.fecha_nacimiento" icon="calendar-today" trap-focus></b-datepicker>
            </b-field>
            <b-field>
                <b-input placeholder="Email" v-model="cliente.email" type="email"></b-input>
            </b-field>
            <b-field>
                <b-input placeholder="Telefono" v-model="cliente.telefono" type="number">
            </b-input>
            </b-field>
            <b-field>
                <b-button type="is-primary" @click="createDoc">Guardar</b-button>
            </b-field>
        </section>
            </div>
          </div>
        </article>
      </div>
    </div>
  </div>
</template>

<script>
const shortid = require('shortid');
const axios = require('axios');

export default {
  name: 'clientes',
  props: {

  },
  data(){
        return {
            cliente:{ id:'', nombre: '', fecha_nacimiento: '', email:'', telefono:'', fotoURL:''},
            clientes: []
        }
    },
  created(){
    this.readDoc();
  },
  methods: {
    async createDoc(){
            axios.post('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/create/cliente', {
            id: shortid.generate(), 
            nombre: this.cliente.nombre, 
            fecha_nacimiento: this.cliente.fecha_nacimiento, 
            email: this.cliente.email, 
            telefono: this.cliente.telefono,
            fotoURL:'https://bulma.io/images/placeholders/1280x960.png'
        })
        .then(function (response) {
            console.log(response);
        })
        .catch(function (error) {
            console.log(error);
        });
        this.letreroRespuesta()
    },
    async readDoc() {
            try {
                let response = await axios.get('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/read/cliente');
                this.clientes = response.data;
                console.log(this.clientes);
            } catch (error) {
                console.error(error);
            }
        },
    letreroRespuesta(){
      this.$buefy.snackbar.open({
        message: 'Cliente agregado',
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
    .containerClientes{
        background-color: #FFF;
        border-radius: 20px;
        width: 500px;
        height: 500px;
    }
</style>