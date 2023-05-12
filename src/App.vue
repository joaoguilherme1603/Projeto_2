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

const carrinhoGamer = ref({
  items: [],
  total: 0
})

let valorTotal = ref(0)

function addCarrinho(jogo) {
  carrinhoGamer.value.items.push({
    id: jogo.id,
    nome: jogo.nome,
    preco: jogo.preco,
    quantidade: jogo.quantidade,
    total: jogo.preco * jogo.quantidade
  });
  carrinhoGamer.value.total += jogo.preco * jogo.quantidade
}

function mais(index) {
  jogos.value[index].quantidade++
  const pos = carrinhoGamer.value.items.indexOf(carrinhoGamer.value.items.find(c => c.id === jogos.value[index].id))
  if (pos != -1) {
    carrinhoGamer.value.total -= carrinhoGamer.value.items[pos].total
    carrinhoGamer.value.items[pos].total = ++carrinhoGamer.value.items[pos].quantidade * carrinhoGamer.value.items[pos].preco
    carrinhoGamer.value.total += carrinhoGamer.value.items[pos].total

  }
}

function menos(index) {
  jogos.value[index].quantidade--
  const pos = carrinhoGamer.value.items.indexOf(carrinhoGamer.value.items.find(c => c.id === jogos.value[index].id))


  if (pos != +1) {
    carrinhoGamer.value.total -= carrinhoGamer.value.items[pos].total
    carrinhoGamer.value.items[pos].total = --carrinhoGamer.value.items[pos].quantidade * carrinhoGamer.value.items[pos].preco
    carrinhoGamer.value.total += carrinhoGamer.value.items[pos].total
  }
}

function limparGamer(){
carrinhoGamer.value.items = []
carrinhoGamer.value.total = 0
}

</script>

<template>    
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <p class="modal-title fs-5" id="exampleModalLabel">Games:</p>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <div v-for="(carrinhoItem, index) in carrinhoGamer.items" :key="index">              
              <strong> {{ carrinhoItem.id }} - {{ carrinhoItem.nome }}</strong>
              <hr>
              <p>Preço BRL: {{ carrinhoItem.preco }} </p> 
              <p>Quantidade: {{ carrinhoItem.quantidade }} </p>
              <p>Preço: {{ carrinhoItem.total }}</p>
            </div>
            
            <p v-if="carrinhoGamer.items.length > 0">Total: {{ carrinhoGamer.total }} BRL</p>
            <p v-else>Nenhum Item</p>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button @click="limparGamer" type="button" class="btn btn-warning">Clear</button>
          </div>
        </div>
      </div>
    </div>

  <div class="barra">
    <h1>PsychGaming</h1>
  </div>
  <div class="container">
    <button type="button" class="btn btn-primary p-3 mt-2 " data-bs-toggle="modal" data-bs-target="#exampleModal">
      🛒 Carrinho
    </button>
    <div class="row">
      <div v-for="(jogo, index) in jogos" :key="jogo.id" class="tema col-3">
        <h1>{{ jogo.id }} - {{ jogo.nome }}</h1>
        <br />
        <h6>Preço: {{ jogo.preco }} BRL</h6>
        <h6>Quantidade: {{ jogo.quantidade }}</h6>

        <button type="button" @click="menos(index)" class="button">-</button>
        <button type="button" @click="addCarrinho(jogo)" class="button">Add</button>
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
  margin-bottom: 20px;
}

p {
  margin: 10px 10px 10px 10px;
  color: black;
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
  border-color: black;
}

button:hover {
  background-color: grey;
  border-color: grey;
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
