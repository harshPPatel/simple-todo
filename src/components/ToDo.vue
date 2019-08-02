<template>
  <li :class="{ completed: todo.isCompleted }">
    <input
      type="checkbox"
      name="isTodoDone"
      :id="todo.id"
      :checked="todo.isCompleted"
      @change="$emit('complete-todo', todo.id)">
    <label :for="todo.id">{{ todo.task }}</label>
    <button @click="$emit('deleteTodo', todo.id)">
      <img src="../assets/cross.png" alt="cross">
    </button>
  </li>
</template>

<script>
export default {
  props: ['todo'],
};
</script>

<style scoped lang="scss">
button {
  border: none;
  outline: none;
  cursor: pointer;
  height: 100%;
  background-color: transparent;
  img {
    height: 24px;
    width: auto;
  }
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  min-height: 50px;
  height: auto;
  border-bottom: 1px solid rgba(#2E2E2E, 0.25);
  color: #2E2E2E;
  padding: 10px 0;

  &.completed {
    label {
      opacity: 0.5;
      text-decoration: line-through;
    }
  }

  input,
  button {
    width: 10%;
  }
  label {
    width: 80%;
    cursor: pointer;
  }
}
</style>
