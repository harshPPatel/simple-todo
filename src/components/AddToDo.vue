<template>
  <form @submit.prevent="submitForm">
    <input type="text" name="todo" id="todo_input" placeholder="Enter Your Task Here...">
    <button type="submit">Add New Task</button>
  </form>
</template>

<script>
export default {
  methods: {
    isValid() {
      console.log('Hi from addTodo Component');
      return false;
    },
    submitForm(e) {
      if (this.isValid()) {
        e.target.todo.value = '';
      }
    },
  },
};
</script>

<style>

</style>
