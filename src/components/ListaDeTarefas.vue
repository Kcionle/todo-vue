<script setup>
import { ref, computed } from 'vue';

const props = defineProps(['estado']);
const tarefasFiltradas = computed(() => {
  const { filtro } = props.estado;

  switch (filtro) {
    case 'pendentes':
      return getTarefasPendentes();
    case 'finalizadas':
      return getTarefasFinalizadas();
    default:
      return props.estado.tarefas;
  }
});

const getTarefasPendentes = () => {
  return props.estado.tarefas.filter(tarefa => !tarefa.finalizada);
};

const getTarefasFinalizadas = () => {
  return props.estado.tarefas.filter(tarefa => tarefa.finalizada);
};
</script>

<template>
  <ul class="list-group mt-4">
    <li class="list-group-item" v-for="tarefa in tarefasFiltradas" :key="tarefa.titulo">
      <input v-model="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
      <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
        {{ tarefa.titulo }}
      </label>
    </li>
  </ul>
</template>



<style scoped>
.done {
  text-decoration: line-through;
}
</style>




  