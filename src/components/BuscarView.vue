<script setup>
    import { ref } from 'vue'

    const titulo = ref('Usuários Cadastrados')
    const texto = ref('Usuário não encontrado')
    const btn = ref('Novo Usuário')
</script>

<template>
    <div class="container">
        <div class="cabecalho">
            <h4>{{ titulo }}</h4>
            <button>{{ btn }}</button>
        </div>
        <div class="buscar">
            <input type="search" placeholder="Buscar usuário">
        </div>
        <div class="texto">
            <h5>{{ texto }}</h5>
        </div>
    </div>
</template>

<style scoped>
    .cabecalho{
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 0px;
        margin-top: 15px;
        margin-bottom: 5px;
    }.cabecalho h4{
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 300;
        color: var(--color-principal);
    }.cabecalho button{
        padding: 7px 15px;
        background: var(--color-principal);
        color: #fff;
        font-size: 14px;
        font-family: Arial, Helvetica, sans-serif;
        border: none;
        border-radius: 5px;
        transition: all .3s;
    }.cabecalho button:hover{
        background-color: var(--color-bg-btnHover);
        transform: scale(1.05);
    }
    .buscar input{
        padding: 7px 10px;
        width: 100%;
        border: none;
        border-bottom: 1px solid #a1a1a1;
        margin-bottom: 5px;
    }
    .texto h5{
        background-color: #fb19195e;
        padding: 10px;
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 300;
        color: rgb(188, 0, 0);
    }

</style>