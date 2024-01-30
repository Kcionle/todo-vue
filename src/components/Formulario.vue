<script setup>
import { defineProps } from 'vue';

const props = defineProps(['estado']);

const adicionarTarefa = () => {
  const novaTarefa = {
    titulo: props.estado.novaTarefa,
    finalizada: false,
  };
  props.estado.tarefas.push(novaTarefa);
  props.estado.novaTarefa = '';
};
</script>

<template>
  <form @submit.prevent="adicionarTarefa">
    <div class="row">
      <div class="col">
        <input v-model="estado.novaTarefa" type="text" placeholder="Digite aqui a descrição da tarefa" class="form-control" required>
      </div>
      <div class="col-md-2">
        <button type="submit" class="btn btn-primary">Cadastrar</button>
      </div>
      <div class="col-md-2">
        <select v-model="estado.filtro" class="form-control">
          <option value="todas">Todas tarefas</option>
          <option value="pendentes">Pendentes</option>
          <option value="finalizadas">Finalizadas</option>
        </select>
      </div>
    </div>
  </form>
</template>


