<template>
  <h2>Cuenta:</h2>
  <h3>{{ saldo }}</h3>
  <h3>{{ estado ? 'activa' : 'desactivada'}}</h3>
  <div v-for="(servicio, index) in servicios" :key="index">
      <p>{{index + 1 }} - {{ servicio }}</p>
  </div>
  <h3>Custom events VUE</h3>
  <Accion 
    texto="aumentar" 
    @acciones="aumentar"
  />
  <Accion 
    texto="disminuir" 
    @acciones="disminuir"
    :desactivar="desactivar"
  />
</template>

<script>
import Accion from '../components/Accion.vue'

export default {
    name: 'cuenta',
    components: {
        Accion
    },
    data() {
        return {
            saldo: 1000,
            tipo: 'visa',
            estado: true,
            servicios: ['react', 'vue', 'angular', 'styled', 'next'],
            desactivar: false
        }
    },
    methods: {
        aumentar(){
            this.saldo = this.saldo + 100
            this.desactivar = false
        },
        disminuir(){
            if(this.saldo === 0) {
                this.desactivar = true
                // alert('yeeep')
                return
            }
            this.saldo = this.saldo - 100
        }
    }
}
</script>

<style>

</style>
