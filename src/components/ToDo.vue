<template>
  <li>
    <input type="checkbox" name="isTodoDone" :id="todo.id" :checked="todo.isCompleted">
    <label :for="todo.id">{{ todo.task }}</label>
  </li>
</template>

<script>
export default {
  props: ['todo'],
};
</script>

<style>
/* Bind class with the value of todo.isCompleted */
</style>
