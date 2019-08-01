<template>
  <ul>
    <ToDo
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      v-on:deleteTodo ="$emit('deleteTodo', todo.id)" />
  </ul>
</template>

<script>
import ToDo from './ToDo.vue';

export default {
  props: ['todos'],
  components: {
    ToDo,
  },
};
</script>

<style>

</style>
