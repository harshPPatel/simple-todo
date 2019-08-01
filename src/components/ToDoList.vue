<template>
  <ul>
    <ToDo
      v-for="todo in todos.slice().reverse()"
      :key="todo.id"
      :todo="todo"
      v-on:deleteTodo ="$emit('deleteTodo', todo.id)"
      v-on:complete-todo ="$emit('complete-todo', todo.id)" />
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
