<script setup>
import { ref } from 'vue'

//Jogos
const jogos = ref ([
    {
        id: 1,
        nome: 'DOOM Eternal',
        preco: 149.00
    },
    {
        id: 2,
        nome: 'Grand Theft Auto V',
        preco: 38.63
    },
    {
        id: 3,
        nome: 'Call Of Duty: Modern Warfare II',
        preco: 299.90
    },
    {
        id: 4,
        nome: 'Minecraft',
        preco: 125.00
    },
    {
        id: 5,
        nome: 'Uncharted: Coleção Legado dos Ladrões',
        preco: 199.90
    },
    {
        id: 6,
        nome: 'The Last Of Us',
        preco: 249.90
    },
    {
        id: 7,
        nome: 'God Of War',
        preco: 199.90
    },
    {
        id: 8,
        nome: 'Dead By Daylight',
        preco: 19.90
    },
    {
        id: 9,
        nome: 'Rainbow Six Siege',
        preco: 23.99
    },
    {
        id: 10,
        nome: 'Half-life Alyx',
        preco: 162.00
    },
    {
        id: 11,
        nome: 'Cuphead',
        preco: 36.99
    },
    
    {
        id: 12,
        nome: 'Hollow Knight',
        preco: 46.99
    },
])

/* const carrinho = ref ([
{
        id: 1,
        nome: 'DOOM Eternal',
        quantidade: 1,
        preco: 149.00,
        valorTotal: 149.90
    },
    {
        id: 2,
        nome: 'Grand Theft Auto V',
        quantidade: 1,
        preco: 38.63,
        valorTotal: 38.63
    },
    {
        id: 3,
        nome: 'Call Of Duty: Modern Warfare II',
        quantidade: 1,
        preco: 299.90,
        valorTotal: 299.99
    },
]) */

</script>
<template>
 <div class="tema col-3">
    <div v-for="(jogo, id) in jogos" :key="id">{{ id }}: {{ jogo.nome }}>
  <h1>Games Disponiveis:</h1>
  <hr>  
  <b>{{ jogos.id }} - {{ jogos.nome }}</b>
  <br>
  <h6>Preço: {{ jogos.preco }}</h6>
  <h6>Quantidade:{{ jogos.quantidade }}</h6>
  <p v-for="(jogo, id) in jogos" :key="id">{{ id }}: {{ jogo.nome }}</p>
  <p v-for="(carrinho, id) in carrinho" :key="id">{{ id }}: {{ carrinho.nome }}</p>
  <button type="button" class="button">-</button>
  <button type="button" class="button">Add</button>
  <button type="button" class="button">+</button>
 </div>
 </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&display=swap');

site-gamer{
  background-color: black;
}
.tema {
  background-color: rgb(0, 0, 0);
  padding: 20px 30px;
  color: rgb(183, 210, 219);
  border-radius: 10px;
  text-align: center;
  display: flex;
  flex-direction: column;
  width: 28%;
  margin: 0 auto;
  margin-top: 12%;
  margin-bottom: 20px;
}

p {
  margin: 15px 15px 15px 15px;
  color: white;
  font-family: monospace;
  font-family: 'Bruno Ace SC', cursive;
}

button {
  font-weight: bold;
  border-radius: 4px;
  color: white;
  background-color: black;
  padding: 5px 10px;
  margin: 15px 15px 15px 15px;
  cursor: pointer;
  font-family: 'Bruno Ace SC', cursive;
}

h1 {
  color: white;
  font-weight: bold;
  font-size: 1.5em;
  font-family: 'Bruno Ace SC', cursive;
}

li {
  margin: 15px 15px 15px 15px;
  color: white;
  font-family: 'Bruno Ace SC', cursive;
}
hr {
    color: white;
}
</style>
