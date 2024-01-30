<script setup>
import { defineProps, computed } from 'vue';

const props = defineProps(['estado']);
const tarefasPendentes = computed(() => getTarefasPendentes().length);

const getTarefasPendentes = () => {
  return props.estado.tarefas.filter(tarefa => !tarefa.finalizada);
};
</script>

<template>
  <header class="p-5 mb-4 mt-4 bg-light rounded-3">
    <h1>Minhas tarefas</h1>
    <p>
      Você possui {{ tarefasPendentes }} tarefas pendentes
    </p>
  </header>
</template>


