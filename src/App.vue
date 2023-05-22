<script setup>
import { ref } from 'vue'

// Produtos no Estoque:
const jogos = ref([
  {
    id: 1,
    nome: 'Uncharted 3: Drake Deception',
    quantidade: 0,
    preco: 199.99,
    img:'https://upload.wikimedia.org/wikipedia/pt/thumb/0/02/Uncharted_3_Boxart.jpg/270px-Uncharted_3_Boxart.jpg'
  },
  {
    id: 2,
    nome: 'Grand Theft Auto V',
    quantidade: 0,
    preco: 38.63,
    img: 'https://s2.glbimg.com/pVUTlvwHrlm44bi3yyYTOElUzw8=/1200x/smart/filters:cover():strip_icc()/i.s3.glbimg.com/v1/AUTH_08fbf48bc0524877943fe86e43087e7a/internal_photos/bs/2021/1/9/8cOmg9TkaB2PgkS1sUjQ/2013-04-02-gta5-capa-rockstar-.jpg'
  },
  {
    id: 3,
    nome: 'Call Of Duty: Modern Warfare II',
    quantidade: 0,
    preco: 299.99,
    img: 'https://sm.ign.com/ign_br/game/c/call-of-du/call-of-duty-modern-warfare-2-1_66u3.jpg'
  },
  {
    id: 4,
    nome: 'Minecraft',
    quantidade: 0,
    preco: 125.0,
    img: 'https://upload.wikimedia.org/wikipedia/pt/9/9c/Minecraft_capa.png'
  },
  {
    id: 5,
    nome: 'DOOM Eternal',
    quantidade: 0,
    preco: 149.0,
    img: 'https://upload.wikimedia.org/wikipedia/pt/8/81/Doom_Eternal_capa.png'
  },
  {
    id: 6,
    nome: 'The Last Of Us',
    quantidade: 0,
    preco: 249.99,
    img: 'https://upload.wikimedia.org/wikipedia/pt/b/be/The_Last_of_Us_capa.png'
  },
  {
    id: 7,
    nome: 'God Of War',
    quantidade: 0,
    preco: 199.99,
    img: 'https://m.media-amazon.com/images/I/81gXqxyFrxL.jpg'
  },
  {
    id: 8,
    nome: 'Dead By Daylight',
    quantidade: 0,
    preco: 19.99,
    img: 'https://upload.wikimedia.org/wikipedia/pt/e/e9/Dead_By_Daylight.png'
  },
  {
    id: 9,
    nome: 'Rainbow Six Siege',
    quantidade: 0,
    preco: 23.99,
    img: 'https://www.mobileupdatebr.com.br/wp-content/uploads/2018/08/Tom-Clancy%E2%80%99s-Rainbow-Six-Siege-capa-200x300.jpg'
  },
  {
    id: 10,
    nome: 'Half-life Alyx',
    quantidade: 0,
    preco: 162.0,
    img: 'https://upload.wikimedia.org/wikipedia/pt/4/49/Half-Life_Alyx_Cover_Art.jpg'
  },
  {
    id: 11,
    nome: 'Cuphead',
    quantidade: 0,
    preco: 36.99,
    img: 'https://upload.wikimedia.org/wikipedia/pt/c/c1/Cuphead_capa.png'
  },

  {
    id: 12,
    nome: 'Hollow Knight',
    quantidade: 0,
    preco: 46.99,
    img: 'https://notadogame.com/uploads/game/cover/250x/5bfdc4cfcdbb6.jpg'
  }
])

// Carrinho:
const carrinhoGamer = ref({
  items: [],
  total: 0
})

// Adicionar Carrinho:
function addCarrinho(jogo) {
  carrinhoGamer.value.items.push({
    id: jogo.id,
    nome: jogo.nome,
    preco: jogo.preco,
    quantidade: jogo.quantidade,
    total: jogo.preco * jogo.quantidade
  })
  carrinhoGamer.value.total += jogo.preco * jogo.quantidade
}

// Adicionar Quantidade
function mais(index) {
  jogos.value[index].quantidade++
  const pos = carrinhoGamer.value.items.indexOf(
    carrinhoGamer.value.items.find((c) => c.id === jogos.value[index].id)
  )
  if (pos != -1) {
    carrinhoGamer.value.total -= carrinhoGamer.value.items[pos].total
    carrinhoGamer.value.items[pos].total =
      ++carrinhoGamer.value.items[pos].quantidade * carrinhoGamer.value.items[pos].preco
    carrinhoGamer.value.total += carrinhoGamer.value.items[pos].total
  }
}

// Subtrair Quantidade
function menos(index) {
  jogos.value[index].quantidade--
  const pos = carrinhoGamer.value.items.indexOf(
    carrinhoGamer.value.items.find((c) => c.id === jogos.value[index].id)
  )

  if (pos != +1) {
    carrinhoGamer.value.total -= carrinhoGamer.value.items[pos].total
    carrinhoGamer.value.items[pos].total =
      --carrinhoGamer.value.items[pos].quantidade * carrinhoGamer.value.items[pos].preco
    carrinhoGamer.value.total += carrinhoGamer.value.items[pos].total
  }
}

// Limpar Carrinho:
function limparGamer() {
  carrinhoGamer.value.items = []
  carrinhoGamer.value.total = 0
}
</script>

<template>

  <!-- Modal: -->
  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <p class="modal-title fs-5" id="exampleModalLabel">Games:</p>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
          <!-- Modal do Carrinho: -->
        </div>
        <div class="modal-body">
          <div v-for="(carrinhoItem, index) in carrinhoGamer.items" :key="index">
            <strong> {{ carrinhoItem.id }} - {{ carrinhoItem.nome }}</strong>
            <hr />
            <p>Preço BRL: {{ carrinhoItem.preco }}</p>
            <p>Quantidade: {{ carrinhoItem.quantidade }}</p>
            <p>Preço/Quantidade: {{ carrinhoItem.total }}</p>
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

  <!-- Codigo da Loja: -->
  <div class="barra">
    <h1>PsychGaming</h1>
  </div>
  <div class="container">
    <button
      type="button"
      class="btn btn-primary p-3 mt-2"
      data-bs-toggle="modal"
      data-bs-target="#exampleModal"
    >
      🛒 Carrinho
    </button>
    <div class="row">
      <div v-for="(jogo, index) in jogos" :key="jogo.id" class="tema col-3">
        <h2>{{ jogo.id }} - {{ jogo.nome }}</h2>
        <img :src="jogo.img" >
        <br />
        <h6>Preço: {{ jogo.preco }} BRL</h6>
        <h6>Quantidade: {{ jogo.quantidade }}</h6>
        
        <!-- Button: -->
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

<!-- CSS: -->
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&family=Press+Start+2P&display=swap');
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
  width: 27%;
  margin: 0 auto;
  margin-top: 8%;
  margin-bottom: 20px;
  border-style:groove;
  box-shadow: 8px 8px 8px black;
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
  border-style:groove;
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
  font-family: 'Press Start 2P', cursive; 
}

h2 {
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
