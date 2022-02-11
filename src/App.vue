<template>
  <div id="app">
    <div class="container">
      <TodoForm @addNewTodo="addTodo"></TodoForm>
      <TodoList
        :todos="todos"
        @markAsComplete="complete"
        @deleteTodoFromList="deleteTodo"
      ></TodoList>
    </div>
  </div>
</template>

<script>
import TodoForm from "./components/todo/TodoForm.vue";
import TodoList from "./components/todo/TodoList.vue";
export default {
  name: "App",
  components: {
    TodoForm,
    TodoList,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
    getAllTodos() {
      // server request to get all todos
      return this.todos;
    },
    complete(index) {
      let todo = this.todos[index];
      todo.completed = !todo.completed;
    },
    deleteTodo(index) {
      // array method splice index of the element to be deleted
      this.todos.splice(index, 1);
    },
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
  margin-top: 60px;
}
</style>
