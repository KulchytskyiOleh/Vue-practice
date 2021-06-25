<template>
  <div class="home">
    <ToDoList msg="Vue ToDo list" />
    <input
      type="text"
      class="todoInput"
      :placeholder="test"
      v-model="inputValue"
    />
    <button v-on:click="addTodo" class="addBtn">add</button>
    <ToDoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @onToggle="isCompleted(todo)"
      @onDelete="todoDelete(todo)"
      @onEdit="editTodo(todo)"
      :isEditing="isEditing"
    />
  </div>
</template>

<script>
import ToDoList from "@/components/ToDoList.vue";
import ToDoItem from "@/components/ToDoItem.vue";
export default {
  name: "Home",
  data() {
    return {
      inputValue: "",
      test: "enter your todo...",
      test1: "Some new todo passed from parent to child",
      todos: [
        { id: 1, title: "My journey with Vue", completed: false },
        { id: 2, title: "Blogging with Vue", completed: true },
        { id: 3, title: "Why Vue is so fun", completed: false },
      ],
      isEditing: false,
      editedTodo: "",
    };
  },
  methods: {
    addTodo() {
      if (this.inputValue.length > 0) {
        this.todos.push({
          id: this.todos.length + 1,
          title: this.inputValue,
          completed: false,
        });
      }
      this.inputValue = "";
    },
    isCompleted(todo) {
      todo.completed = !todo.completed;
      console.log(todo);
    },
    todoDelete(deleteTodo) {
      console.log("test", deleteTodo);
      this.todos = this.todos.filter((todo) => todo != deleteTodo);
    },
    editTodo(editedTodo) {
      this.todos.filter((todo) => {
        if (todo === editedTodo) {
          this.isEditing = !this.isEditing;
          console.log(editedTodo);
          console.log(this.isEditing);
        }
      });
    },
  },
  components: {
    ToDoList,
    ToDoItem,
  },
};
</script>
<style scoped>
input.todoInput {
  max-width: 45vh;
  padding: 10px;
}
div.home {
  margin: 0 auto;
  width: 50%;
  border: 1px solid black;
}
.addBtn {
  padding: 10px;
  margin-left: 5px;
}
</style>
