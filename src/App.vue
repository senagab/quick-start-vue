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
const imgTrueDetective = "https://files.meiobit.com/wp-content/uploads/2020/01/20200129matthew_mcconaughey_1.jpg"

const botaoEstaDesabilitado = false

const gostaDeFilme = false
const gostaDeTvShow = false

const estaAutorizado = true
</script>

<template>
  <h1>{{ dizOla("paula") }}</h1>
  <img v-if="gostaDeFilme" :src="enderecoDaImagem" alt="">
  <img v-else-if="gostaDeTvShow" :src="imgTrueDetective" alt="">
  <h2 v-else>
    Não curte filmes e tv shows
  </h2>

  <h1 v-if="estaAutorizado">Bem vindo</h1>
  <h1 v-else>Não possui acesso</h1>

  <button :disabled="!botaoEstaHabilitado">enviar mensagem</button>
</template>

<style scoped>

img {
  max-width: 200px;
}
</style>
