<template>
  <div class="cadastro">
    <h1>Cadastro de Livros</h1>
    
    <input v-model="novoLivro.autor" placeholder="Autor" />
    <input v-model="novoLivro.descricao" placeholder="Nome do livro" />
    <select v-model="novoLivro.categoria">
      <option value="" disabled selected>Categoria</option>
      <option value="Terror">Terror</option>
      <option value="Romance">Romance</option>
      <option value="Ficção">Ficção</option>
    </select>
    
    <button @click="adicionarLivro">Cadastrar Livro</button>
    
    <button @click="irParaListaLivros">Ver Livros Cadastrados</button>  

    <button @click="irParaTelaInicial">Voltar tela inicial</button>  
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { useLivrosStore } from '../stores/livros'  // Importando o store para manipular o estado global

const router = useRouter()

const novoLivro = ref({
  autor: '',
  descricao: '',
  categoria: ''
})

const livrosStore = useLivrosStore()  // Usando o store para acessar o estado global de livros

// Função para adicionar um livro ao estado global
function adicionarLivro() {
  if (novoLivro.value.autor && novoLivro.value.descricao && novoLivro.value.categoria) {
    livrosStore.adicionarLivro(novoLivro.value)  // Adicionando o livro ao Pinia (store)
    novoLivro.value = { autor: '', descricao: '', categoria: '' }  // Limpando os campos após adicionar
  }
}

// Função para ir para a tela de listagem de livros
function irParaListaLivros() {
  router.push('/TelaLivros')  // Navega para a tela de listagem de livros
}

function irParaTelaInicial() {
  router.push('/')  // Navega para a tela de listagem de livros
}
</script>

<style scoped>
/* Estilo da tela de cadastro */
.cadastro {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  background-color: #f9f9f9;
}

h1 {
  text-align: center;
}

input,
select {
  width: 100%;
  padding: 10px;
  margin: 5px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  background-color: #ff69b4; /* Rosa */
  color: white;
  padding: 8px; /* Menor altura */
  font-size: 14px; /* Reduzido */
  border: none;
  border-radius: 20px; /* Mais arredondado */
  cursor: pointer;
  width: 100%;
  margin: 5px 0;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

button:hover {
  background-color: #ff1493; /* Um tom mais escuro de rosa */
  transform: scale(1.05); /* Efeito de crescimento ao passar o mouse */
}

button:active {
  background-color: #c71585; /* Rosa ainda mais escuro ao clicar */
  transform: scale(0.95); /* Efeito de clique */
}
</style>
