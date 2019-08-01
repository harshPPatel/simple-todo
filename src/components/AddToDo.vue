<template>
  <form @submit.prevent="submitForm">
    <input type="text" name="todo" id="todo_input" placeholder="Enter Your Task Here...">
    <button type="submit">Add New Task</button>
  </form>
</template>

<script>
import uuid from 'uuid/v1';

export default {
  methods: {
    isValid() {
      console.log('Hi from addTodo Component');
      return true;
    },
    submitForm(e) {
      if (this.isValid()) {
        e.target.todo.value = '';
        console.log(uuid());
      }
    },
  },
};
</script>

<style>

</style>
