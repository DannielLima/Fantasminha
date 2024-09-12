<template>
    <div>
      <div v-if="!isScared" class="normal-page">
        <h1>Preencha o Formulário</h1>
        <p>Preencha este formulário tranquilamente e depois clique em Enviar.</p>
        <form @submit.prevent="handleSubmit">
          <input type="text" v-model="formData" placeholder="Digite algo..." />
          <button type="submit">Enviar</button>
        </form>
      </div>
  
      <!-- Jumpscare Section -->
      <div v-if="isScared" class="jumpscare">
        <img src="/scary-image.jpg" alt="Scary face" class="scary-image" />
        <audio ref="scream" autoplay>
          <source src="/scream.mp3" type="audio/mpeg" />
        </audio>
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref } from 'vue';
  
  export default defineComponent({
    name: 'Jumpscare',
    setup() {
      const isScared = ref(false);
      const formData = ref('');
  
      const handleSubmit = () => {
        setTimeout(() => {
          isScared.value = true; // Ativa o jumpscare
          const audioElement = document.querySelector('audio');
          audioElement?.play();  // Toca o som assustador
        }, 3000); // Espera 3 segundos para dar o susto
      };
  
      return {
        formData,
        isScared,
        handleSubmit
      };
    }
  });
  </script>
  
  <style scoped>
  .normal-page {
    text-align: center;
    padding: 20px;
  }
  
  input {
    padding: 10px;
    font-size: 16px;
    margin-bottom: 10px;
  }
  
  button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #28a745;
    color: white;
    border: none;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #218838;
  }
  
  .jumpscare {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: black;
    z-index: 9999;
  }
  
  .scary-image {
    width: 100%;
    height: 100%;
    max-width: 600px;
    max-height: 600px;
    object-fit: cover;
  }
  </style>
  