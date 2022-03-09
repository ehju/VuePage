<template>
  <PageHeader />
  <TodoInput />
  <TodoList />
  <PageFooter />
</template>

<script>
import PageHeader from "./components/PageHeader.vue";
import PageFooter from "./components/PageFooter.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  components: {
    PageHeader: PageHeader,
    PageFooter: PageFooter,
    TodoInput: TodoInput,
    TodoList: TodoList,
  },
  data() {
    return {
      todoItems: [],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
