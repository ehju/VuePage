<template>
  <div>
    <input
      type="text"
      v-model="newTodoItem"
      placeholder="할일을 입력하자!"
      v-on:keyup.enter="addTodo"
    />
    <button v-on:click="addTodo">추가</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: "",
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoItem != "") {
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit("addTodo", value);
        this.clearInput();
      }
    },
  },
};
</script>

<style>
</style>