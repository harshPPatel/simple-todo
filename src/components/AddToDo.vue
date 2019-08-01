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
        this.error = this.task !== '' ? 'Please enter valid input!' : '';
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

<style lang="scss" scoped>
  form {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;

    input,
    button {
      height: 50px;
      border-radius: 100px;
      outline: none;
      border: none;
      font-size: 20px;
      font-family: "Muli", sans-serif;
      font-weight: 700;
    }

    input {
      background-color: #fff;
      border: 4px solid #42CDE7;
      color: #2E2E2E;
      padding: 0 40px;
      margin-right: 16px;

      ::placeholder {
        color: rgba(#2E2E2E, 0.1)
      }
    }

    button {
      cursor: pointer;
      padding:  0 30px;
      background-color: #42CDE7;
      color: #fff;
      opacity: 1;
      transition: all 0.2s ease-in-out;
      display: inline-block;

      &:hover {
        opacity: 0.8;
      }
      &:disabled {
        opacity: 0.5;
      }
    }
  }

  p {
    text-align: center;
    color: #e74c3c;
    font-size: 24px;
    margin: 10px 0 20px;
  }
</style>
