<script setup>
import { ref, computed } from 'vue'
import InformacoesView from './InformacoesView.vue';
import CadastradosView from './CadastradosView.vue';
import BuscarView from './BuscarView.vue';

const alunos = ref([
])
const termoBusca = ref('')
const formKey = ref(0)

const alunosFiltrados = computed(() => {
    if (!termoBusca.value) return alunos.value

    const termo = termoBusca.value.toLowerCase()

    return alunos.value.filter(aluno =>
    aluno.nome.toLowerCase().includes(termo) ||
    aluno.username.toLowerCase().includes(termo) ||
    aluno.email.toLowerCase().includes(termo)
    )
})

const buscarAluno = (valor) => {
    termoBusca.value = valor
}

const semResultado = computed(() =>
    termoBusca.value && alunosFiltrados.value.length === 0
)

const modoEdicao = ref(false)
const alunoEmEdicao = ref(null)

const excluir = (id) => {
    alunos.value = alunos.value.filter(aluno => aluno.id !== id)
}

const erroUsername = ref('')
const usernameExiste = (username, idAtual = null) => {
    return alunos.value.some(aluno => aluno.username === username && aluno.id !== idAtual)
}

const cadastrarAluno = (aluno) => {
    if(usernameExiste(aluno.username)){
        erroUsername.value = 'Username já está em uso'
        return
    }

    alunos.value.push({
        id: Date.now(),
        ...aluno
    })

    erroUsername.value = ''
    alunoEmEdicao.value = null
    formKey.value++
}


const editarAluno = (aluno) => {
    modoEdicao.value = true
    alunoEmEdicao.value = {...aluno}
}

const salvarEdicao = (alunoAtualizado) => {
    const index = alunos.value.findIndex(a => a.id === alunoAtualizado.id)
    if (index !== -1) {
        alunos.value[index] = alunoAtualizado
    }

    modoEdicao.value = false
    alunoEmEdicao.value = null
}

const novoUsuario = () => {
    modoEdicao.value = false
    alunoEmEdicao.value = null
}


</script>

<template>
    <div>
        <InformacoesView
        :key="formKey"
        :modo-edicao="modoEdicao"
        :aluno="alunoEmEdicao"
        :erro-username="erroUsername"
        @cadastrar="cadastrarAluno"
        @salvar="salvarEdicao"
        />
        <BuscarView
        :sem-resultado="semResultado"
        @novo-usuario="novoUsuario"
        @buscar="buscarAluno"
        />
        <CadastradosView 
        :alunos="alunosFiltrados"
        @editar="editarAluno" 
        @excluir="excluir"
        />
    </div>
</template>