<template>
  <li>
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
/* Bind class with the value of todo.isCompleted */
button {
  img {
    height: 24px;
    width: auto;
  }
}
</style>
