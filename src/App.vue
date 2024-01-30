<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue';

const estado = reactive({
  filtro: 'todas',
  tarefaTemp: '',
  tarefas: [
    {
      titulo: 'Estudar ES6',
      finalizada: false,
    },
    {
      titulo: 'Estudar SASS',
      finalizada: false,
    },
    {
      titulo: 'Estudar HTML',
      finalizada: false,
    },
  ],
  novaTarefa: '',
});
</script>

<template>
  <div class="container">
    <Cabecalho :estado="estado" />
    <Formulario :estado="estado" />
    <ListaDeTarefas :estado="estado" />
  </div>
</template>




