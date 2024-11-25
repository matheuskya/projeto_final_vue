<template>
  <div class="lista-livros">
    <h1>Lista de Livros Cadastrados</h1>
    
    <ul v-if="livros.length > 0">
      <li v-for="(livro, index) in livros" :key="index">
        {{ livro.autor }} - {{ livro.descricao }} ({{ livro.categoria }})
        <button @click="removerLivro(index)">Deletar</button>
      </li>
    </ul>
    
    <p v-else>Nenhum livro cadastrado.</p>

    <button @click="voltarParaCadastro">Voltar para o Cadastro</button>
  </div>
</template>

<script setup>
import { useLivrosStore } from '../stores/livros'  // Importando o store para acessar o estado global de livros
import { useRouter } from 'vue-router'

const livrosStore = useLivrosStore()  // Usando o Pinia para acessar os livros
const router = useRouter()

// Acessando a lista de livros no Pinia
const livros = livrosStore.livros

// Função para remover um livro
function removerLivro(index) {
  livrosStore.removerLivro(index)  // Remove o livro do store
}

// Função para voltar para o cadastro
function voltarParaCadastro() {
  router.push('/MeuComponent')  // Navega para a tela de cadastro
}
</script>

<style scoped>
.lista-livros {
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
  font-family: 'Arial', sans-serif;
  color: #ff1493; /* Rosa vibrante */
  font-size: 1.8rem;
  margin-bottom: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #ccc;
  font-family: 'Arial', sans-serif;
  font-size: 1rem;
  color: #555;
}

li:last-child {
  border-bottom: none;
}

/* Botões estilizados */
button {
  background-color: #ff69b4; /* Rosa vibrante */
  color: white;
  padding: 10px 15px;
  font-family: 'Arial', sans-serif;
  font-size: 0.9rem;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 1px;
  border: none;
  border-radius: 30px; /* Botões arredondados */
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.2s ease;
}

button:hover {
  background-color: #ff1493; /* Rosa mais escuro */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transform: scale(1.05);
}

button:active {
  background-color: #c71585; /* Rosa ainda mais escuro */
  transform: scale(0.95);
}

/* Mensagem quando não há livros */
p {
  text-align: center;
  font-family: 'Arial', sans-serif;
  font-size: 1.2rem;
  color: #777;
}

/* Botão de voltar com destaque */
button:last-child {
  margin-top: 20px;
  width: 100%; /* Botão largo */
}
</style>


