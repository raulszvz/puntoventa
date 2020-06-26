<template>
  <div class="nuevoProducto">
     <div class="containerNuevoProducto">
         <section class="subContainer">
            <strong>Nuevo Producto</strong>
            <b-field>
                <b-input placeholder="Modelo" v-model="producto.modelo"></b-input>
            </b-field>
            <b-field>
                <b-input placeholder="Marca" v-model="producto.marca"></b-input>
            </b-field>
            <b-field>
                <b-select placeholder="Tipo" v-model="producto.tipo" expanded>
                    <option value="Tops">Tops</option>
                    <option value="Camisas y blusas">Camisas y blusas</option>
                    <option value="Ropa para dormir">Ropa para dormir</option>
                    <option value="Lencería">Lencería</option>
                    <option value="Básicos">Básicos</option>
                    <option value="Trajes de baño">Trajes de baño</option>
                    <option value="Pantalones">Pantalones</option>
                    <option value="Jeans">Jeans</option>
                    <option value="Shorts">Shorts</option>
                    <option value="Faldas">Faldas</option>
                    <option value="Accesorios">Accesorios</option>
                    <option value="Blazers">Blazers</option>
                    <option value="Suéteres">Suéteres</option>
                    <option value="Calcetines">Calcetines</option>
                    <option value="Chamarras y abrigos">Chamarras y abrigos</option>
                    <option value="Sudaderas">Sudaderas</option>
                </b-select>
            </b-field>
            <b-field>
                <b-select placeholder="Talla" v-model="producto.talla" expanded>
                    <option value="XS">XS</option>
                    <option value="S">S</option>
                    <option value="M">M</option>
                    <option value="L">L</option>
                    <option value="XL">XL</option>
                </b-select>
            </b-field>
            <b-field>
                <b-input placeholder="Precio" v-model="producto.precio"></b-input>
            </b-field>
            <b-field>
                <b-input placeholder="Existencias" v-model="producto.existencias"></b-input>
            </b-field>
            <b-field>
                <b-input type="textarea"
                    minlength="10"
                    maxlength="100"
                    placeholder="Descripción"
                    v-model="producto.descripcion">
                </b-input>
            </b-field>
            <b-field>
                <b-button type="is-primary" @click="createDoc">Guardar</b-button>
            </b-field>
        </section>
     </div>
  </div>
</template>

<script>
const shortid = require('shortid');
const axios = require('axios');

export default {
  name: 'nuevoProducto',
  props: {

  },
  data(){
        return {
            producto:{ modelo:'', marca:'', tipo:'', talla:'', descripcion:'', precio:'', existencias:'', imgURL:''}
        }
    },
  methods: {
    async createDoc(){
            axios.post('https://us-central1-sweetjazmin-api.cloudfunctions.net/app/api/create/producto', {
            id: shortid.generate(), 
            modelo: this.producto.modelo, 
            marca: this.producto.marca, 
            tipo: this.producto.tipo, 
            talla: this.producto.talla, 
            descripcion: this.producto.descripcion, 
            precio: this.producto.precio, 
            existencias: this.producto.existencias, 
            imgURL:'https://bulma.io/images/placeholders/1280x960.png'
        })
        .then(function (response) {
            console.log(response);
        })
        .catch(function (error) {
            console.log(error);
        });
    }
  }
}
</script>

<style>
    .containerNuevoProducto{
        background-color: #FFF;
        border-radius: 20px;
        width: 500px;
        height: 600px;
    }
    .subContainer{
        padding: 5%;
    }
</style>