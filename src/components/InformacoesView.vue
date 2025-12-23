<script setup>
    import { ref } from 'vue'

    const titulo = ref('Novo Usuário')
    const btn1 = ref('Cancelar')
    const btn2 = ref('Cadastrar')
</script>

<template>
    <div class="main">
        <p>{{ titulo }}</p>
        <div class="inputs">
            <input type="text" placeholder="Digite seu nome...">
            <input type="text" placeholder="Digite o usename">
            <input type="email" placeholder="Digite o e-mail">
        </div>
        <div class="btns">
            <button>{{ btn1 }}</button>
            <button>{{ btn2 }}</button>
        </div>
    </div>
</template>

<style scoped>
    .main{
        display: flex;
        flex-direction: column;
        width: 100%;
    }
    .inputs{
        display: flex;
        flex-direction: column;
        gap: 10px;
        margin-top: -5px;
    }.inputs input{
        padding: 10px 20px;
        width: 500px;
    }
    .btns{
        margin-top: 10px;
        display: flex;
        gap: 5px;
    }.btns button{
        padding: 5px 15px;
    }
</style>