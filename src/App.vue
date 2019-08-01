<template>
  <div id="app">
    <Header/>
    <addTodo />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import addTodo from './components/AddToDo.vue';

export default {
  name: 'app',
  components: {
    Header,
    addTodo,
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
