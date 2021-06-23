<template>
    <button :disabled="desactivar" @click="acciones">{{ texto }}</button>
</template>

<script>
export default {
    name: 'accion',

    props: {
        texto: String,
        desactivar: {
            type: Boolean,
            default: false
        }
    },
    methods: {
      acciones() {
          this.$emit('acciones')
      }  
    },
}
</script>

<style>
    
</style>