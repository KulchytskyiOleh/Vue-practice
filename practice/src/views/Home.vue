<template>
  <div class="home">
    <ToDoList msg="Vue ToDo list" />
    <!-- <form @submit.prevent="addTodo()"> -->
    <input
      type="text"
      class="todoInput"
      :placeholder="test"
      v-model="inputValue"
      @keyup.enter="addTodo"
    />
    <!-- </form> -->
    <!-- <button v-on:click="addTodo" class="addBtn">add</button> -->
    <ToDoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @onToggle="isCompleted(todo)"
      @onDelete="todoDelete(todo)"
      @onEdit="editTodo(todo)"
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
      editedTodo: "",
      isEditing: false,
      test: "enter your todo...",
      todos: [
        {
          id: 1,
          title: "My journey with Vue",
          completed: false,
          isEditing: false,
        },
        {
          id: 2,
          title: "Blogging with Vue",
          completed: true,
          isEditing: false,
        },
        {
          id: 3,
          title: "Why Vue is so fun",
          completed: false,
          isEditing: false,
        },
      ],
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
    },
    todoDelete(deleteTodo) {
      this.todos = this.todos.filter((todo) => todo != deleteTodo);
    },
    editTodo(editedTodo) {
      this.todos.filter((todo) =>
        todo.id === editedTodo.id
          ? (todo.isEditing = !editedTodo.isEditing)
          : todo.isEditing
      );
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
  max-width: 50vh;
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
