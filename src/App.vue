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
@import url(./assets/base.css);
@import url(./assets/main.css);

  .principal{
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: var(--color-bg);
  }
  .geral{
    border-radius: 20px;
    padding: 25px;
    width: 800px;
    background-color: #fff;
  }

  .logo{
    text-align: right;
  }.logo img{
    height: 50px;
  }

  .titulo{
    text-align: center;
  }.titulo h1{
    font-family: 'Laila', serif;
    font-weight: 400;
    font-size: 36px;
    color: var(--color-principal);
  }

  
</style>
