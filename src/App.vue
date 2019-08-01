<template>
  <div id="app">
    <Header/>
    <AddTodo />
    <ToDoList />
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
          todo: 'task1',
          isComplete: false,
        },
        {
          id: 2,
          todo: 'task2',
          isComplete: false,
        },
        {
          id: 3,
          todo: 'task3',
          isComplete: false,
        },
      ];
    }
  },
  components: {
    Header,
    AddTodo,
    ToDoList,
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
