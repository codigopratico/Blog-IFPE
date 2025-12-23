<script setup>
  import { ref } from 'vue'
  import BuscarView from './components/BuscarView.vue';
  import CadastradosView from './components/CadastradosView.vue';
  import InformacoesView from './components/InformacoesView.vue';

  const titulo = ref('Blog IFPE')
</script>

<template>
  <div class="principal">
    <div class="geral">
      <div class="logo">
        <img src="./img/Logo.png" alt="Logo IF">
      </div>
      <div class="titulo">
        <h1>{{ titulo }}</h1>
      </div>

      <InformacoesView/>

      <BuscarView/>

      <CadastradosView />
    </div>
  </div>
</template>

<style scoped>
@import url(./assets/main.css);

  .principal{
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .geral{
    border: 1px solid #000;
    padding: 15px;
    width: 600px;
  }

  .logo{
    text-align: right;
  }.logo img{
    height: 50px;
  }

  .titulo{
    text-align: center;
  }

  
</style>
