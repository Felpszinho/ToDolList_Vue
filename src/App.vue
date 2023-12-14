<script setup>
import { reactive } from "vue";
import Cabecalho from "./components/Cabecalho.vue";
import Formulario from "./components/Formulario.vue";
import ListaDeTarefas from "./components/LIstaDeTarefas.vue";
const estado = reactive({
  filtro: "todas",
  tarefaTemp: "",
  tarefas: [
    {
      titulo: "Estudar ES6",
      finalizada: false,
    },
    {
      titulo: "Estudar sass",
      finalizada: false,
    },
    {
      titulo: "Ir para a academia",
      finalizada: true,
    },
  ],
});
const getTarefasPendentes = () => {
  return estado.tarefas.filter((tarefa) => !tarefa.finalizada);
};
const getTarefasFinalizadas = () => {
  return estado.tarefas.filter((tarefa) => tarefa.finalizada);
};
const getTarefasFiltradas = () => {
  const { filtro } = estado;
  switch (filtro) {
    case "pendentes":
      return getTarefasPendentes();
    case "finalizadas":
      return getTarefasFinalizadas();
    default:
      return estado.tarefas;
  }
};
const cadastrarTarefas = (e) => {
  e.preventDefault();
  
  const tarefanova = {
    titulo: estado.tarefaTemp,
    finalizada: false,
  };
  estado.tarefas.push(tarefanova);
  estado.tarefaTemp = "";
};
</script>

<template>
  <div class="container">
    <Cabecalho :tarefaspendentes="getTarefasPendentes().length" />
    <Formulario
      :trocar-filtro="(evento) => estado.filtro=evento.target.value"
      :tarefa-temp="estado.tarefaTemp"
      :edita-tarefa-temp="evento=> estado.tarefaTemp = evento.target.value"
      :cadastra-tarefa="cadastrarTarefas"
    />

    <ListaDeTarefas :tarefas="getTarefasFiltradas()" />
  </div>
</template>

<style scoped></style>
