<template>
  <div class="nuevoProducto">
     <div class="containerNuevoProducto">
         <section class="subContainer">
            <strong>Nuevo Producto</strong>
            <b-field>
                <b-input placeholder="Email" type="email"></b-input>
            </b-field>
            <b-field>
                <b-input placeholder="Number"
                    type="number"
                    min="10"
                    max="20">
                </b-input>
            </b-field>

            <b-field>
                <b-input placeholder="User handle (custom validation for only lowercase)"
                    type="text"
                    required
                    validation-message="Only lowercase is allowed"
                    pattern="[a-z]*">
                </b-input>
            </b-field>

            <b-field>
                <b-input placeholder="URL" type="url"></b-input>
            </b-field>

            <b-field>
                <b-input type="textarea"
                    minlength="10"
                    maxlength="100"
                    placeholder="Maxlength automatically counts characters">
                </b-input>
            </b-field>
            <b-field>
                <b-button type="is-primary">Guardar</b-button>
            </b-field>
        </section>
     </div>
  </div>
</template>

<script>
//import uuidv4 from 'uuid/v4'

export default {
  name: 'nuevoProducto',
  props: {

  }
}
</script>

<style>
    .containerNuevoProducto{
        background-color: #FFF;
        border-radius: 20px;
        width: 500px;
        height: 500px;
    }
    .subContainer{
        padding: 5%;
    }
</style>