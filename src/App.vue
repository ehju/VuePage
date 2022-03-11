<template>
  <PageHeader />
  <TodoInput v-on:addTodo="addTodo" />
  <TodoList
    v-bind:propsdata="todoItems"
    @removeTodo="removeTodo"
    @changeTodoState="changeTodoState"
  />
  <PageFooter v-if="todoItems.length > 0" v-on:clearAllTodo="removeAll" />
</template>

<script>
import PageHeader from "./components/PageHeader.vue";
import PageFooter from "./components/PageFooter.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  //최상위 컴포넌트에 todoItems 데이터를 정의하고 하위 TodoList 에 props 로 전달
  data() {
    return {
      todoItems: [],
    };
  },
  methods: {
    //TodoInput 에서 addTodo 이벤트 발생했을 때 실행
    addTodo(todoItem) {
      let obj = { item: todoItem, completed: false };
      localStorage.setItem(obj.item, JSON.stringify(obj));
      this.todoItems.push(obj);
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    changeTodoState(todoItem) {
      todoItem.completed = !todoItem.completed;
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    },
    removeAll() {
      localStorage.clear();
      this.todoItems = [];
    },
  },
  created() {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) != "loglevel:webpack-dev-server") {
          let todoObj = JSON.parse(localStorage.getItem(localStorage.key(i)));
          this.todoItems.push(todoObj);
        }
      }
    }
  },
  components: {
    PageHeader: PageHeader,
    PageFooter: PageFooter,
    TodoInput: TodoInput,
    TodoList: TodoList,
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
input {
  width: 300px;
}
</style>
