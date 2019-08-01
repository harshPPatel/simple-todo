<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:addTodo="addTodo" />
    <ToDoList
      :todos="this.todos"
      v-on:deleteTodo="deleteTodo"
      v-on:complete-todo="completeTodo" />
    <footer>
      Made with 💓.
      <a href="https://github.com/harshPPatel/simple-todo" target="_blank"> Go to GitHub</a>
    </footer>
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
      const todos = localStorage.getItem('todos');
      this.todos = JSON.parse(todos);
    } else {
      this.todos = [
        {
          id: 3,
          task: 'Delete tasks',
          isCompleted: false,
        },
        {
          id: 2,
          task: 'Complete the tasks which are done',
          isCompleted: true,
        },
        {
          id: 1,
          task: 'Add your own task',
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
  updated() {
    // Saving todos to localStorage
    if (this.todos.length > 0) {
      const todos = JSON.stringify(this.todos);
      localStorage.setItem('todos', todos);
    }
  },
  methods: {
    addTodo(todo) {
      this.todos = [...this.todos, todo];
    },
    deleteTodo(id) {
      const todos = this.todos.filter(todo => todo.id !== id);
      this.todos = todos;
    },
    completeTodo(id) {
      // Changing completeTodo of todo
      this.todos.forEach((todo) => {
        if (todo.id === id) {
          todo.isCompleted = !todo.isCompleted;
        }
      });
      // Updating todos in local storage
      localStorage.setItem('todos', JSON.stringify(this.todos));
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  height: 100vh;
  width: 100%;
  position: relative;
  font-size: 20px;
}
#app {
  font-family: "Muli", Helvetica, Arial, sans-serif;
  font-weight: 700;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: auto;
}

</style>
