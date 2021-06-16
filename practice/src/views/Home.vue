<template>
  <div class="home">
    <ToDoList msg="Vue ToDo list" />
    <input type="text" class='todoInput'/>
    <ToDoItem />
  </div>
</template>

<script>
import ToDoList from '@/components/ToDoList.vue';
import ToDoItem from '@/components/ToDoItem.vue';

export default {
  name: 'Home',
  components: {
    ToDoList,
    ToDoItem,
  },
};
</script>
<style scoped>
input.todoInput{
  width: 50vh;
  padding: 10px;
}
div.home {
  margin: 0 auto;
  width: 50%;
  border: 1px solid black;
}
</style>
