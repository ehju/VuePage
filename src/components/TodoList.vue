<template>
  <section>
    <ul v-if="propsdata.length > 0">
      <li
        v-for="(todoItem, index) in propsdata"
        v-bind:key="todoItem.item"
        :class="{ completed: todoItem.completed }"
      >
        <i
          class="checkBtn fa fa-check"
          aria-hidden="true"
          @click="changeTodoState(todoItem, index)"
        ></i>
        {{ todoItem.item }}
        <span
          class="removeBtn"
          type="button"
          @click="removeTodo(todoItem, index)"
        >
          <i class="fa fa-trash" aria-hidden="true"></i>
        </span>
      </li>
    </ul>
    <div v-else>
      <i class="emptyBox fas fa-calendar-check fa-xl" aria-hidden="true"></i>
    </div>
  </section>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    removeTodo(todoItem, index) {
      this.$emit("removeTodo", todoItem, index);
    },
    changeTodoState(todoItem, index) {
      this.$emit("changeTodoState", todoItem, index);
    },
  },
};
</script>

<style>
ul {
  list-style-type: none;
  text-align: left;
  padding-left: 1rem;
  margin-top: 0px;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.2em 0;
  padding: 0 1em;
}
.checkBtn {
  line-height: 50px;
  margin-right: auto;
}
.removeBtn {
  margin-left: auto;
  margin-right: 15px;
}
.emptyBox {
  text-align: center;
  margin-top: 5rem;
  font-size: 20rem;
  color: #d1dffa;
}
.completed {
  text-decoration-line: line-through;
  color: gray;
}
</style>
