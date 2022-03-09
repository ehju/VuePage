<template>
  <section>
    <ul>
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem">
        <i class="checkBtn fa fa-check" aria-hidden="true"></i>
        {{ todoItem }}
        <span
          class="removeBtn"
          type="button"
          @click="removeTodo(todoItem, index)"
        >
          <i class="fa fa-trash" aria-hidden="true"></i>
        </span>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
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
</style>