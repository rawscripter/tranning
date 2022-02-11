<template>
  <div class="todo-form">
    <div class="card">
      <div class="card-body">
        <div class="form-group">
          <div class="row">
            <div class="col-10">
              <input
                type="text"
                v-model="todoForm.title"
                placeholder="Add todo your todo list"
                class="form-control"
              />
            </div>
            <div class="col-2">
              <button @click="storeTodoList" class="btn btn-primary btn-block">
                Add
              </button>
            </div>
          </div>

          <div v-if="isError" class="alert alert-danger mt-4">
            {{ errorMessage }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoForm",
  data() {
    return {
      todoForm: {
        id: null,
        title: "",
        completed: false,
      },
      isError: false,
      errorMessage: "",
    };
  },
  methods: {
    storeTodoList() {
      this.isError = false;
      if (this.todoForm.title == "") {
        this.isError = true;
        this.errorMessage = "Todo title is required";
        return;
      }
      // make a axios request to server to store todo list
      this.todoForm.id = new Date().getTime();
      this.$emit("addNewTodo", this.todoForm);

      this.todoForm = {
        id: null,
        title: "",
        completed: false,
      };
    },
  },
};
</script>


<style scoped>
.btn-block {
  width: 100%;
}
</style>