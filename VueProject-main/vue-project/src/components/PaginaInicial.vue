<template>
  <div class="inicio">
    <h1>Bem-vindo ao Gerenciador de Livros</h1>
    <p>Clique abaixo para cadastrar novos livros:</p>
    <button @click="irParaCadastro">Cadastre livros aqui</button>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router' // Usando o Vue Router para navegação

const router = useRouter()

function irParaCadastro() {
  router.push('/MeuComponent') // Redireciona para a rota de cadastro
}
</script>

<style scoped>
/* Remove padding/margins do body e faz o fundo cobrir toda a tela */
.inicio {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  margin: 0; /* Remove qualquer margem */
  padding: 0; /* Remove qualquer padding */
  text-align: center;
  background: linear-gradient(-45deg, #ff9a9e, #fad0c4, #fbc2eb, #a18cd1);
  background-size: 300% 300%;
  animation: gradientAnimation 8s ease infinite;
  font-family: 'Arial', sans-serif;
}

/* Faz o body também cobrir toda a tela */
body {
  margin: 0;
  padding: 0;
  height: 100vh;
  overflow: hidden; /* Garante que não apareçam barras de rolagem */
}

/* Animação do fundo */
@keyframes gradientAnimation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

/* Título principal */
h1 {
  font-size: 2.5rem;
  color: #000; /* Cor preta */
  margin-bottom: 10px;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1); /* Leve sombreado */
}

/* Parágrafo */
p {
  font-size: 1.2rem;
  color: #000; /* Cor preta */
  margin-bottom: 20px;
}

/* Botão */
button {
  background-color: rgba(255, 255, 255, 0.8);
  color: #000000;
  padding: 12px 24px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
  font-weight: bold;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); /* Sombra para destacar o botão */
  transition: background-color 0.3s ease, transform 0.2s ease; /* Efeito suave */
}

button:hover {
  background-color: rgba(255, 255, 255, 1);
  transform: scale(1.05); /* Aumenta ligeiramente o tamanho */
}

button:active {
  transform: scale(0.95); /* Reduz ligeiramente o tamanho ao clicar */
}
</style>
