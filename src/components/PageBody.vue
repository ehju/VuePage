<template>
  <TodoInput />
  <TodoList />
</template>

<script>
import TodoInput from "./TodoInput.vue";
import TodoList from "./TodoList.vue";
export default {
  components: {
    TodoInput: TodoInput,
    TodoList: TodoList,
  },
};
</script>

<style>
</style>