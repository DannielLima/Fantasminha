<template>
    <div>
      <div v-if="!isScared" class="normal-page">
        <h1>Compartilhe Seus Pensamentos</h1>
        <p>Conte-nos um pouco sobre seus pensamentos. Após preencher, clique em Enviar.</p>
        <form @submit.prevent="handleSubmit">
          <input type="text" v-model="formData" placeholder="Digite algo..." />
          <button type="submit">Enviar</button>
        </form>
      </div>
  
      <div v-if="isScared" class="jumpscare">
        <img src="/scary-image.jpg" alt="Scary face" class="scary-image" />
        <audio ref="scream" autoplay>
          <source src="/scream.mp3" type="audio/mpeg" />
        </audio>
      </div>
  
      <footer class="footer">
        <p>Desenvolvido por <a href="https://github.com/DannielLima" target="_blank" rel="noopener noreferrer">Danniel Lima</a></p>
      </footer>
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
          isScared.value = true;
          const audioElement = document.querySelector('audio');
          audioElement?.play();
          if (window.navigator.vibrate) {
            window.navigator.vibrate([500, 200, 500, 200, 500]);
          }
        }, 3000);
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
    max-width: 100%;
    box-sizing: border-box;
  }
  
  input {
    padding: 10px;
    font-size: 16px;
    margin-bottom: 10px;
    width: calc(100% - 22px);
    box-sizing: border-box;
  }
  
  button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #28a745;
    color: white;
    border: none;
    cursor: pointer;
    width: 100%;
    max-width: 200px;
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
  
  .footer {
    position: fixed;
    bottom: 0;
    width: 100%;
    text-align: center;
    padding: 10px;
    background-color: #f1f1f1;
  }
  
  .footer a {
    color: #007bff;
    text-decoration: none;
  }
  
  .footer a:hover {
    text-decoration: underline;
  }
  
  @media (max-width: 768px) {
    .normal-page {
      padding: 10px;
    }
  
    input {
      font-size: 14px;
      padding: 8px;
    }
  
    button {
      font-size: 14px;
      padding: 8px 16px;
    }
  
    .scary-image {
      max-width: 100%;
      max-height: 100%;
    }
  }
  </style>  