<template>
  <div>
    <form @submit.prevent="submitForm">
      <input
        v-model="task"
        type="text"
        name="todo"
        id="todo_input"
        placeholder="Enter Your Task Here..."
        required
        @input="validateInput"
        autofocus
      >
      <button type="submit" :disabled="!isValid">Add New Task</button>
    </form>
    <p id="error">{{ error }}</p>
  </div>
</template>

<script>
import uuid from 'uuid/v1';

export default {
  data: () => ({
    task: '',
    isValid: false,
    error: '',
  }),
  methods: {
    validateInput() {
      if (this.task !== '' && this.task.trim() !== '') {
        this.isValid = true;
        this.error = '';
      } else {
        this.isValid = false;
        this.error = 'Please enter valid input!';
      }
    },
    submitForm() {
      if (this.isValid) {
        // Creating unique id
        let id = uuid();

        // Checking if the unique id already exists in localStorage todos or not
        if (localStorage.getItem('todos')) {
          const todos = JSON.parse(localStorage.getItem('todos'));
          todos.forEach((todo) => {
            if (todo.id === id) {
              // If exists, creaeting new unique id
              id = uuid();
            }
          });
        }

        const todo = {
          id,
          task: this.task,
          isCompleted: false,
        };

        // Emitting the event
        this.$emit('addTodo', todo);

        // Setting data to default stage
        this.task = '';
        this.isValid = false;
      }
    },
  },
};
</script>

<style>

</style>
