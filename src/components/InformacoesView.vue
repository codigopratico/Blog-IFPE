<script setup>
    import { ref } from 'vue'

    const titulo = ref('Novo Usuário')
    const btn1 = ref('Cancelar')
    const btn2 = ref('Cadastrar')
</script>

<template>
    <div class="main">
        <h4>{{ titulo }}</h4>
        <div class="inputs">
            <input type="text" placeholder="Digite seu nome...">
            <input type="text" placeholder="Digite o usename...">
            <input type="email" placeholder="Digite o e-mail...">
        </div>
        <div class="btns">
            <button>{{ btn1 }}</button>
            <button>{{ btn2 }}</button>
        </div>
    </div>
</template>

<style scoped>
    @import '../assets/base.css';

    .main{
        display: flex;
        flex-direction: column;
        width: 100%;
    }
    .inputs{
        display: flex;
        flex-direction: column;
        gap: 10px;
        margin-top: 5px;
    }.inputs input{
        padding: 12px 15px;
        width: 100%;
        border: 1px solid var(--color-principal);
        border-radius: 15px;
    }
    .btns{
        margin-top: 10px;
        display: flex;
        gap: 5px;
    }.btns button{
        padding: 7px 20px;
        border-radius: 5px;
        border: none;
        font-size: 14px;
        transition: all 0.3s;
        cursor: pointer !important;
    }.btns button:first-child{
        background-color: rgba(255, 0, 0, 0.841);
        color: #fff;
    }button:first-child:hover{
        background-color: #b3092bec;
        transform: scale(1.05);
    }
    .btns button:nth-child(2){
        background-color: var(--color-principal);
        color: #fff;
    }.btns button:nth-child(2):hover{
        background-color: var(--color-bg-btnHover);
        transform: scale(1.05);
    }
    h4{
        color: var(--color-principal);
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 500;
        font-size: 17px;
    }
</style>