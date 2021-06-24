<template>
  <div class="home">
    <ToDoList msg="Vue ToDo list" />
    <input type="text" class="todoInput" :placeholder="test" v-model="test3" />
    <ToDoItem :test1="test1" :msg1="msg1" />
  </div>
</template>

<script>
import ToDoList from "@/components/ToDoList.vue";
import ToDoItem from "@/components/ToDoItem.vue";
export default {
  data() {
    return {
      test: "enter your todo...",
      test1: "Some new todo passed from parent to child",
      test3: "",
    };
  },
  name: "Home",
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
