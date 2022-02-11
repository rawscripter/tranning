<template>
  <div class="todo-form mt-5">
    <div class="card mb-3" v-for="(todo, index) in todos" :key="todo.id">
      <div
        class="card-body p-2 d-flex justify-content-between align-items-center"
        :class="todo.completed ? 'is-complete' : ''"
      >
        <div class="left-section">{{ todo.title }}</div>
        <div
          class="
            right-section
            d-flex
            justify-content-between
            align-items-center
          "
        >
          <div class="btn-group">
            <button
              @click="markAsComplete(index)"
              class="btn btn-primary btn-sm"
              v-if="!todo.completed"
            >
              Mark as Complete
            </button>
            <button
              v-if="todo.completed"
              @click="markAsComplete(index)"
              class="btn btn-warning btn-sm"
            >
              Mark as Not Complete
            </button>
            <!-- <button class="btn btn-info btn-sm">Edit</button> -->
            <button
              @click="deleteTodoFromList(index)"
              class="btn btn-danger btn-sm"
            >
              Delete
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: ["todos"],
  data() {
    return {};
  },
  methods: {
    markAsComplete(index) {
      //   let todo = this.todos[index];
      //   todo.completed = !todo.completed;
      this.$emit("markAsComplete", index);
    },
    deleteTodoFromList(index) {
      this.$emit("deleteTodoFromList", index);
      // array method splice index of the element to be deleted
      //   this.todos.splice(index, 1);
    },
  },
};
</script>


<style scoped>
.is-complete {
  background-color: #00800052;
}
</style>