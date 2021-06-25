<template>
  <div class="Item">
    <p>{{ todo.id }} {{ todo.title }}</p>
  </div>
</template>

<script>
export default {
  name: "ToDoItem",
  props: {
    test1: String,
    test2: String,
    todo: Object,
  },
  data() {
    return {
     
    };
  },
};
</script>

<style scoped>
div.Item {
  display: grid;
  margin: 20px;
}
p {
  display: flex;
  justify-content: center;
  justify-self: center;
  width: 50%;
  padding: 5px;
  margin: 10px;
  border: 1px solid blue;
}
</style>
