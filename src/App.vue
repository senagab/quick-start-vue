<script setup>
const nome = "gabriel"
const meuObjeto = {
  nome: "gian",
  filmeFavorito: "Dazed and Confused"
}

function dizOla(nome) {
  return `${nome} diz oi`;
}

const enderecoDaImagem = "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTepEI3ooX-xTWxqducQ90dHkaN0rJdUcFWpyoUfrGJPVv4PkNzvpfsK2trZy1MPN4KaAo&usqp=CAU"

const botaoEstaDesabilitado = false
</script>

<template>
  <h1>{{ dizOla("paula") }}</h1>
  <img :src="enderecoDaImagem" alt="">

  <button :disabled="!botaoEstaHabilitado">enviar mensagem</button>
</template>

<style scoped>
</style>
