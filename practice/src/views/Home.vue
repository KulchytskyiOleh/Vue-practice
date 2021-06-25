<template>
  <div class="home">
    <ToDoList msg="Vue ToDo list" />
    <input
      type="text"
      class="todoInput"
      :placeholder="test"
      v-model="inputValue"
    />
    <button v-on:click="addTodo">add</button>
    <ToDoItem v-for="todo in todos" :key="todo.id" :todo="todo" />
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
        { id: 1, title: "My journey with Vue" },
        { id: 2, title: "Blogging with Vue" },
        { id: 3, title: "Why Vue is so fun" },
      ],
    };
  },
  methods: {
    addTodo() {
      this.todos.push({ id: this.todos.length + 1, title: this.inputValue });
      this.inputValue = "";
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
  width: 50vh;
  padding: 10px;
}
div.home {
  margin: 0 auto;
  width: 50%;
  border: 1px solid black;
}
</style>
