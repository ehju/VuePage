<template>
  <div class="inputBox shadow">
    <input
      type="text"
      v-model="newTodoItem"
      placeholder="할 일을 입력하자!"
      v-on:keyup.enter="addTodo"
    />
    <span class="addContainer" v-on:click="addTodo"
      ><i class="addBtn fa fa-plus" aria-hidden="true"></i
    ></span>
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
input:focus {
  outline: none;
}
.inputBox {
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
  margin: 1em;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
  background: none;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: inline-block;
  border-radius: 0 5px 5px 0;
  width: 3rem;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>