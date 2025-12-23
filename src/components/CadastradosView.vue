<script setup>
    const alunos = [
        {id: 1, nome: 'Kauan Gabriel', email: 'kg2370124@gmail.com', username: 'kauan123'},
    ]
</script>
<template>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css"/>
    <table id="tabela">
        <tr id="topo">
            <td>Nome</td>
            <td>Email</td>
            <td>Username</td>
            <td></td>
        </tr>
        <tr class="conteudo" v-for="aluno in alunos" :key="aluno.id">
            <td>{{ aluno.nome }}</td>
            <td>{{ aluno.email }}</td>
            <td>{{ aluno.username }}</td>
            <td id="icones">
                <i class="bi bi-pencil"></i>
                <i class="bi bi-trash"></i>
            </td>
        </tr>
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
        font-size: 17px;
    }
</style>