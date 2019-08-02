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

<style lang="scss" scoped>
  ul {
    background-color: #fff;
    box-shadow: 0 0 6px rgba(black, 0.16);
    border-radius: 24px;
    max-height: 300px;
    overflow-y: scroll;
    height: 100%;
    list-style: none;
    margin-top: 24px;
    max-width: 550px;
    margin: 0 auto;

    @media (max-width: 550px) {
      width: 85%;
    }
  }
</style>
