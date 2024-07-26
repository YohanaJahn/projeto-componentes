<script setup>

const teste = defineProps(['usuario'])
console.log(teste.usuario)
</script>
<template>
  <div>
    <h1>Informações do Usuário</h1>
    <div class="perfil">
      <p>Nome: {{ usuario.nome }}</p>
      <p>E-mail: {{ usuario.email }}</p>
      <p>Data de Nascimento: {{ usuario.dataNascimento }}</p>
      <p>Endereço: {{ usuario.endereco }}</p>
      <p>Cidade: {{ usuario.cidade }}</p>
      <p>Estado: {{ usuario.estado }}</p>
      <p>Hobbies: {{ usuario.hobbies }}</p>
      <p>Linguagens de Programação: {{ usuario.linguagens }}</p>
      <p>Biografia: {{ usuario.biografia }}</p>
    </div>
  </div>
</template>
