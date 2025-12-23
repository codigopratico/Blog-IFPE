<script setup>
    import { ref } from 'vue'

    const titulo = ref('Usuários Cadastrados')
    const texto = ref('Usuário não encontrado')
    const btn = ref('Novo Usuário')
</script>

<template>
    <div class="container">
        <div class="cabecalho">
            <p>{{ titulo }}</p>
            <button>{{ btn }}</button>
        </div>
        <div class="buscar">
            <input type="search" placeholder="Buscar usuário">
        </div>
        <div class="texto">
            <p>{{ texto }}</p>
        </div>
    </div>
</template>

<style scoped>
    .cabecalho{
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: -10px;
    }.cabecalho button{
        padding: 3px 10px;
    }
    .buscar input{
        padding: 7px 10px;
        width: 100%;
        border: none;
        border-bottom: 1px solid #a1a1a1;
        margin-bottom: -10px;
    }
    .texto p{
        background-color: red;
        padding: 10px;
    }

</style>