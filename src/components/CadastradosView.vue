<script setup>
const emit = defineEmits(['excluir', 'editar'])

const { alunos } = defineProps({
  alunos: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <table id="tabela">

    <thead>
      <tr id="topo">
        <td>Nome</td>
        <td>Email</td>
        <td>Username</td>
        <td></td>
      </tr>
    </thead>

    <tbody v-if="alunos.length > 0">
      <tr class="conteudo" v-for="aluno in alunos" :key="aluno.id">
        <td>{{ aluno.nome }}</td>
        <td>{{ aluno.email }}</td>
        <td>{{ aluno.username }}</td>
        <td id="icones">
          <i class="bi bi-pencil" @click="emit('editar', aluno)"></i>
          <i class="bi bi-trash" @click="emit('excluir', aluno.id)"></i>
        </td>
      </tr>
    </tbody>
    
    <tbody v-else>
        <tr>
            <td colspan="4" style="text-align: center; padding: 15px;">Nenhum aluno Cadastrado</td>
        </tr>
    </tbody>

  </table>
</template>

<style scoped>
    #tabela{
        width: 100%;
        border-collapse: collapse;
        margin-top: 5px;
    }
    #tabela #topo{
        background-color: var(--color-principal);
        color: #fff;
        width: 100%;
    }
    #tabela tr td{
        border-bottom: 1px solid #999;
    }#tabela #topo td{
        background-color: var(--color-bg-btn);
        font-size: 16px;
        padding: 5px;
    }#tabela .conteudo td{
        padding: 10px;
    }
    img{
        width: 20px;
    }
    i:first-child{
        color: blue;
    }
    i:nth-child(2){
        color: red;
    }#icones{
        display: flex;
        gap: 5px;
    }
</style>