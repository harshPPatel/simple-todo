<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:addTodo="addTodo" />
    <ToDoList :todos="this.todos" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import AddTodo from './components/AddToDo.vue';
import ToDoList from './components/ToDoList.vue';

export default {
  name: 'app',
  data: () => ({
    todos: [],
  }),
  created() {
    if (localStorage.getItem('todos')) {
      this.todos = localStorage.getItem('todos');
    } else {
      this.todos = [
        {
          id: 1,
          task: 'task1',
          isCompleted: false,
        },
        {
          id: 2,
          task: 'task2',
          isCompleted: false,
        },
        {
          id: 3,
          task: 'task3',
          isCompleted: false,
        },
        {
          id: 4,
          task: 'task3',
          isCompleted: false,
        },
        {
          id: 5,
          task: 'task3',
          isCompleted: false,
        },
      ];
    }
  },
  components: {
    Header,
    AddTodo,
    ToDoList,
  },
  methods: {
    addTodo(todo) {
      this.todos = [...this.todos, todo];
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
