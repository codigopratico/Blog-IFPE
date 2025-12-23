<script setup>
  import { ref } from 'vue'
  import AlunosView from './components/AlunosView.vue';

  const titulo = ref('Blog IFPE')
</script>

<template>
  <form class="principal">
    <div class="geral">
        <div class="logo">
          <img src="./img/Logo.png" alt="Logo IF">
        </div>
        <div class="titulo">
          <h1>{{ titulo }}</h1>
        </div>
        <hr id="linha">
      <AlunosView />
    </div>
  </form>
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
    padding: 25px;
    background-color: var(--color-cinza-claro);
    border-radius: 16px;
  }
  .geral{
    border-radius: 20px;
    padding: 20px 30px 10px 30px;
    width: 800px;
    background-color: var(--color-branco);
    box-shadow:
    0 6px 20px rgba(0, 0, 0, 0.2),
    0 14px 30px rgba(0, 0, 0, 0.10);
  }
  .logo{
    float: right;
  }.logo img{
    height: 65px;
  }

  .titulo{
    margin-top: 10px;
    text-align: center;
    margin-bottom: 10px;
  }.titulo h1{
    font-weight: 400;
    font-size: 36px;
    color: var(--color-verde-ifpe);
  }
  #linha{
    width: 100%;
    margin-bottom: 25px;
    border: 1px solid var(--color-verde-secundario);
  }

  
</style>
