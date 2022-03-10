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
    <modal :show="showModal" @close="showModal = false">
      <template #header>
        <h3>Warning!</h3>
      </template>
      <template #body> 할 일을 입력하세요. </template>
    </modal>
  </div>
</template>

<script>
import Modal from "./common/Modal.vue";

export default {
  data() {
    return {
      newTodoItem: "",
      showModal: false,
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoItem != "") {
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit("addTodo", value);
        this.clearInput();
      } else {
        this.showModal = true;
      }
    },
    clearInput() {
      this.newTodoItem = "";
    },
  },
  components: {
    Modal: Modal,
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