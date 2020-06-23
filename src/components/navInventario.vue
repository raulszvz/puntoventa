<template>
  <div class="navInventario">
     <b-navbar class="is-light">
        <template slot="brand">
            <b-navbar-item>
                <img
                    src="https://raw.githubusercontent.com/buefy/buefy/dev/static/img/buefy-logo.png"
                    alt="Lightweight UI components for Vue.js based on Bulma"
                >
            </b-navbar-item>
        </template>
        <template slot="start">
            <b-navbar-item @click="modalClientes = true">
                 <b-icon icon="account-group"></b-icon>
            </b-navbar-item>
            <b-navbar-item @click="modalCodigoBarras = true">
                <b-icon icon="barcode"></b-icon>
            </b-navbar-item>
            <b-navbar-item @click="modalNuevoProducto = true">
                <b-icon icon="plus-circle-outline"></b-icon>
            </b-navbar-item>
            <!--<b-navbar-dropdown label="Info">
                <b-navbar-item href="#">
                    About
                </b-navbar-item>
                <b-navbar-item href="#">
                    Contact
                </b-navbar-item>
            </b-navbar-dropdown>-->
            <div class="modalNavInv">
                <b-modal :active.sync="modalClientes"
                    trap-focus
                    :destroy-on-hide="false"
                    aria-role="dialog"
                    aria-modal>
                    <clientes/>
                </b-modal>
                <b-modal :active.sync="modalCodigoBarras"
                    trap-focus
                    :destroy-on-hide="false"
                    aria-role="dialog"
                    aria-modal>
                    <codigoBarras/>
                </b-modal>
                <b-modal :active.sync="modalNuevoProducto"
                    trap-focus
                    :destroy-on-hide="false"
                    aria-role="dialog"
                    aria-modal>
                    <nuevoProducto/>
                </b-modal>
            </div>
        </template>
        <template slot="end">
            <b-navbar-item tag="div">
                <b-button class="is-light"><b-icon icon="github"></b-icon></b-button>
            </b-navbar-item>
        </template>
    </b-navbar>
  </div>
</template>

<script>
import clientes from './../components/clientes.vue'
import codigoBarras from './../components/codigoBarras.vue'
import nuevoProducto from './../components/nuevoProducto.vue'

export default {
  name: 'navInventario',
  components: {
    clientes,
    codigoBarras,
    nuevoProducto
  },
  props: {

  },
  data(){
        return {
            modalClientes: false,
            modalCodigoBarras: false,
            modalNuevoProducto: false,
        }
    }
}
</script>

<style>
    .clientes{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .codigoBarras{
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>
