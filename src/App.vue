<script setup>
import { ref } from 'vue'
import Formulario from './components/Formulario.vue'
import Informacoes from './components/Informacoes.vue'


const mostrarFormulario = ref(true)
const usuario = ref({})
function fazerMostrar(novoUsuario){
  usuario.value = {...novoUsuario.value}
  mostrarFormulario.value = !mostrarFormulario.value
}
</script>
<template>
  <div>
    <transition name="form" mode="out-in">
      <Formulario v-if="mostrarFormulario" @mostrarFormulario="fazerMostrar"/>
      <Informacoes v-else :usuario="usuario" />
    </transition>
  </div>
</template>