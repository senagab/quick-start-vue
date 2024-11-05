<script setup>
import { reactive } from 'vue';

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

// let contador = 0
const estado = reactive({
  contador: 0,
  email: '',
  saldo: 5000,
  transferindo: 0,
  nomes: ['madalena', 'rob', 'olivia', 'godofredo', 'eloise'],
  nomeAInserir: '',
})

function incrementar() {
    estado.contador++;
    console.log('aumentou')
}

function decrementar() {
  estado.contador--;
  console.log('diminuiu')
}

function alteraEmail(evento) {
  estado.email = evento.target.value;
}

function mostraSaldoFuturo() {
  const { saldo, transferindo } = estado;
  return saldo - transferindo;
}

function validaValorTransferencia() {
  const { saldo, transferindo } = estado;
  return saldo >= transferindo;
}

function cadastraNome() {
  if (estado.nomeAInserir.length >= 3) {

    estado.nomes.push(estado.nomeAInserir)
  } else {
    alert("digite mais caracteres")
  }
  // console.log(estado);
}

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

  <br>
  <br>

  {{ estado.contador }}

  <button @click="incrementar" type="button">+</button>
  <button @click="decrementar" type="button">-</button>

  <br>
  <br>

  {{ estado.email }}
  <input type="email" @keyup="alteraEmail">

  <br>
  <br>

  Saldo: {{ estado.saldo }} <br>
  Transferindo: {{ estado.transferindo }} <br>
  Saldo depois da transferencia: {{ mostraSaldoFuturo() }} <br><br>
  <input class="campo" :class="{ invalido: !validaValorTransferencia() }" @keyup="evento => estado.transferindo = evento.target.value " type="number" placeholder="quantia para transferir">
  <button v-if="validaValorTransferencia()">Transferir</button>
  <span v-else>Valor maior que o saldo disponível</span>

  <br>
  <br>

  <ul>
    <li v-for="nome in estado.nomes">
      {{ nome }}
    </li>
  </ul>

  <input @keyup="evento => estado.nomeAInserir = evento.target.value" type="text" placeholder="digite um novo nome">
  <button @click="cadastraNome()" type="button">cadastrar nome</button>

  <h3 v-for="nome in estado.nomes">
    {{ nome }}
  </h3>

</template>

<style scoped>

img {
  max-width: 200px;
}

.invalido {
  outline-color: red;
  border-color: red;
}

.campo {
  border: 2px solid #000;
}
</style>
