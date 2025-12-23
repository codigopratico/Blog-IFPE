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
            <input type="text" placeholder="Digite seu nome..." v-model="nome" required>
            <input type="text" placeholder="Digite o username..." v-model="username" required>
            <p v-if="props.erroUsername" class="erro">
                {{ props.erroUsername }}
            </p>
            <input type="email" placeholder="Digite o e-mail..." v-model="email" required>
        </div>
        <div class="btns">
            <button @click="cancelar">{{ btn1 }}</button>
            <button @click="submit">{{ modoEdicao ? 'Salvar' : btn2 }}</button>
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

    .erro {
        color: red;
        font-size: 13px;
        margin-top: 4px;
    }

</style>