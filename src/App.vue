<script setup>
import { ref } from 'vue'

const jogos = ref([
  {
    id: 1,
    nome: 'Uncharted 3: Drake Deception',
    quantidade: 0,
    preco: 199.99
  },
  {
    id: 2,
    nome: 'Grand Theft Auto V',
    quantidade: 0,
    preco: 38.63
  },
  {
    id: 3,
    nome: 'Call Of Duty: Modern Warfare II',
    quantidade: 0,
    preco: 299.99
  },
  {
    id: 4,
    nome: 'Minecraft',
    quantidade: 0,
    preco: 125.0
  },
  {
    id: 5,
    nome: 'DOOM Eternal',
    quantidade: 0,
    preco: 149.0
  },
  {
    id: 6,
    nome: 'The Last Of Us',
    quantidade: 0,
    preco: 249.99
  },
  {
    id: 7,
    nome: 'God Of War',
    quantidade: 0,
    preco: 199.99
  },
  {
    id: 8,
    nome: 'Dead By Daylight',
    quantidade: 0,
    preco: 19.99
  },
  {
    id: 9,
    nome: 'Rainbow Six Siege',
    quantidade: 0,
    preco: 23.99
  },
  {
    id: 10,
    nome: 'Half-life Alyx',
    quantidade: 0,
    preco: 162.0
  },
  {
    id: 11,
    nome: 'Cuphead',
    quantidade: 0,
    preco: 36.99
  },

  {
    id: 12,
    nome: 'Hollow Knight',
    quantidade: 0,
    preco: 46.99
  }
])
</script>
<template>
  <div class="barra">
    <h1>PsychGaming</h1>
  </div>
  <div class="container">
    <div class="row">
      <div v-for="(jogo, index) in jogos" :key="jogo.id" class="tema col-3">
        <h1>{{ jogo.id }} - {{ jogo.nome }}</h1>
        <br />
        <h6>Preço: {{ jogo.preco }} BRL</h6>
        <h6>Quantidade: {{ jogo.quantidade }}</h6>

        <button type="button" @click="menos(index)" class="button">-</button>
        <button type="button" @click="addCarrinho(index)" class="button">Add</button>
        <button type="button" @click="mais(index)" class="button">+</button>
      </div>
    </div>
  </div>
  <div class="barra">
    <h1>Alisson Fernandes</h1>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&display=swap');
.barra {
  text-align: center;
  font-size: 50px;
}
.tema {
  background-color: rgb(0, 0, 0);
  padding: 20px 30px;
  color: rgb(183, 210, 219);
  border-radius: 10px;
  text-align: center;
  display: flex;
  flex-direction: column;
  width: 30%;
  margin: 0 auto;
  margin-top: 8%;
  margin-bottom: 10px;
}

p {
  background-color: black;
  margin: 10px 10px 10px 10px;
  color: white;
  font-family: monospace;
  font-family: 'Bruno Ace SC', cursive;
}

button {
  font-weight: bold;
  border-radius: 4px;
  color: white;
  background-color: black;
  padding: 5px 5px;
  margin: 10px 10px 10px 10px;
  cursor: pointer;
  font-family: 'Bruno Ace SC', cursive;
}

h1 {
  background-color: black;
  color: white;
  font-weight: bold;
  font-size: 1.5em;
  font-family: 'Bruno Ace SC', cursive;
}

hr {
  color: white;
}
h6 {
  background-color: black;
  color: white;
  font-weight: bold;
  font-size: 20px;
  font-family: 'Bruno Ace SC', cursive;
}
</style>
