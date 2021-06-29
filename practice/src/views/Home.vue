<template>
  <div class="home">
    <ToDoList msg="Vue ToDo list" />
    <input
      type="text"
      class="todoInput"
      :placeholder="test"
      v-model="inputValue"
      @keyup.enter="addTodo"
    />
    <!-- <button v-on:click="addTodo" class="addBtn">add</button> -->
    <ToDoItem
      v-for="todo in todosData"
      :key="todo.id"
      :todo="todo"
      @onToggle="isCompleted(todo)"
      @onDelete="todoDelete(todo)"
      @onEdit="editTodo"
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
      todosData: JSON.parse(localStorage.getItem("todos")) || [
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
        this.todosData.push({
          id: Date.now(),
          title: this.inputValue,
          completed: false,
          isEditing: false,
        });
      }
      this.inputValue = "";
      this.saveData();
    },
    isCompleted(todo) {
      todo.completed = !todo.completed;
      this.saveData();
    },
    todoDelete(deleteTodo) {
      this.todosData = this.todosData.filter((todo) => todo != deleteTodo);
      this.saveData();
    },
    editTodo(editedTodo, editedTitle) {
      this.todosData.findIndex((todo) => todo.id === editedTodo);
      this.todosData = this.todosData.map((el) => {
        if (el.id === editedTodo) {
          el.title = editedTitle;
        }
        return el;
      });
      this.saveData();
    },
    saveData() {
      const storageData = JSON.stringify(this.todosData);
      localStorage.setItem("todos", storageData);
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
  width: 50%;
  padding: 15px;
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
