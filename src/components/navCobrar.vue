<template>
  <div class="navCobrar">
     <div class="iconCodigoBarrasLector" @click="modalCodigoBarrasLector = true">
        <b-button class="is-white"><b-icon icon="barcode-scan"></b-icon></b-button>
     </div>
     <div class="modalNavCob">
                <b-modal :active.sync="modalCodigoBarrasLector"
                    trap-focus
                    :destroy-on-hide="false"
                    aria-role="dialog"
                    aria-modal>
                    <codigoBarrasLector/>
                </b-modal>
            </div>
  </div>
</template>

<script>
import codigoBarrasLector from './../components/codigoBarrasLector.vue'

export default {
  name: 'navCobrar',
  components: {
    codigoBarrasLector
  },
  props: {

  },
  data(){
        return {
            modalCodigoBarrasLector: false,
        }
    }
}
</script>

<style>
    .codigoBarrasLector{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .iconCodigoBarrasLector{
        padding-top: 8px;
        padding-left: 15px;
    }
</style>
