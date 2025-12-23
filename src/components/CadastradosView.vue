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
            <td colspan="4" style="text-align: center; padding: 15px; color: var(--color-cinza-escuro);">Nenhum aluno Cadastrado</td>
        </tr>
    </tbody>

  </table>
  <div class="verde-escuro"></div>
  <div class="verde-claro"></div>
</template>

<style scoped>
    #tabela{
        width: 100%;
        border-collapse: collapse;
        margin-top: 5px;
    }
    #tabela #topo{
        background-color: var(--color-principal);
        color: var(--color-branco);
        width: 100%;
    }
    #tabela tr td{
        border-bottom: 1px solid var(color-cinza-claro);
    }#tabela #topo td{
        background-color: var(--color-verde-ifpe);
        font-size: 16px;
        padding: 5px 15px;
    }#tabela #topo td:first-child{
      border-radius: 10px 0 0 0;
    }
    #tabela .conteudo td{
        padding: 10px;
    }
    img{
        width: 20px;
    }
    i:first-child{
        color: var(--color-azul);
    }
    i:nth-child(2){
        color: var(--color-vermelho-ifpe);
    }#icones{
        display: flex;
        gap: 5px;
    }
    .verde-escuro{
      height: 10px;
      background-color: var(--color-verde-ifpe);
    }
    .verde-claro{
      height: 10px;
      background-color: var(--color-verde-secundario);
      border-radius: 0 0 5px 5px;
    }
</style>