<script setup>
    import { ref, watch } from 'vue'

    const titulo = ref('Novo Usuário')
    const btn1 = ref('Cancelar')
    const btn2 = ref('Cadastrar')

    const emit = defineEmits(['cadastrar', 'salvar'])

    const erroFormulario = ref('')

    const props = defineProps({
        modoEdicao: Boolean,
        aluno: Object,
        erroUsername: String
    })

    const nome = ref('')
    const username = ref('')
    const email = ref('')

    const validarFormulario = () => {
    if (!nome.value || !username.value || !email.value) {
        erroFormulario.value = 'Preencha todos os campos'
        return false
    }

  const emailValido = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  if (!emailValido.test(email.value)) {
    erroFormulario.value = 'E-mail inválido'
    return false
  }

  erroFormulario.value = ''
  return true
}


    watch(() => props.aluno, (novoAluno) => {
        if (novoAluno) {
            nome.value = novoAluno.nome
            username.value = novoAluno.username
            email.value = novoAluno.email
        } else {
            limparformulario()
        }
    })

    const limparformulario = () => {
        nome.value = ''
        username.value = ''
        email.value = ''
    }

    const submit = () => {
        if (!validarFormulario()) return

        if (props.modoEdicao) {
        emit('salvar', {
            id: props.aluno.id,
            nome: nome.value,
            username: username.value,
            email: email.value
        })
        } else {
            emit('cadastrar', {
            nome: nome.value,
            username: username.value,
            email: email.value
        })
    }
}


    const cancelar = () => {
        limparformulario()
    }
</script>

<template>
    <div class="main">
        <h4>{{ titulo }}</h4>
        <div class="inputs">
            <div class="input">
                <i class="fa-solid fa-user"></i>
                <input type="text" placeholder="Digite seu nome..." v-model="nome" required>
            </div>
            <div class="input">
                <i class="fa-solid fa-at"></i>
                <input type="text" placeholder="Digite seu usuário..." v-model="username" required>
            </div>
            <p v-if="props.erroUsername" class="erro">
                {{ props.erroUsername }}
            </p>
            <div class="input">
                <i class="fa-solid fa-envelope"></i>
                <input type="email" placeholder="Digite seu e-mail..." v-model="email" required>
            </div>
        </div>
        <div class="btns">
            <button @click="cancelar" type="button">{{ btn1 }}</button>
            <button @click="submit" type="button">{{ modoEdicao ? 'Salvar' : btn2 }}</button>
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
    
    }.inputs .input{
        display: flex;
        align-items: center;
    }.inputs .input i{
        font-size: 26px;
        color: var(--color-branco);
        padding: 10px;
        background-color: var(--color-verde-ifpe);
        border-radius: 10px 0 0 10px;
    }.inputs input{
        padding: 12px 15px;
        width: 100%;
        border: 1.5px solid var(--color-verde-secundario);
        border-radius: 0 15px 15px 0;
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
        background-color: var(--color-vermelho-ifpe);
        color: #fff;
    }button:first-child:hover{
        background-color: #b3092bec;
        transform: scale(1.05);
    }
    .btns button:nth-child(2){
        background-color: var(--color-verde-ifpe);
        color: #fff;
    }.btns button:nth-child(2):hover{
        background-color: var(--color-verde-secundario);
        transform: scale(1.05);
    }
    h4{
        color: var(--color-verde-ifpe);
        font-weight: 450;
        font-size: 17px;
    }

    .erro {
        color: var(--color-vermelho-ifpe);
        font-size: 13px;
        margin-top: 4px;
    }

</style>