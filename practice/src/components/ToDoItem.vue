<template>
  <div class="Item">
    <input
      type="checkbox"
      @click="$emit('onToggle')"
      :checked="todo.completed"
      class="todoCheckbox"
    />
    <p @click="$emit('onToggle')" :class="todo.completed ? 'completed' : null">
      {{ todo.title }}
    </p>
    <button v-if="isEditing" class="saveEdited" @click="$emit('onEdit')">
      &#x1F4BE;
    </button>
    <button class="editTodo" @click="$emit('onEdit')">&#9997;</button>
    <button class="deleteTodo" @click="$emit('onDelete')">&#x274C;</button>
  </div>
</template>

<script>
export default {
  name: "ToDoItem",
  props: {
    test1: String,
    test2: String,
    todo: Object,
    isEditing: Boolean,
    // onToggle: Function,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
div.Item {
  display: grid;
  grid-template-areas: "checkbox title editTodo deleteTodo";
  margin: 20px auto;
  border: 1px solid #000000;
  width: 50%;
}
p {
  display: grid;
  grid-area: title;
  justify-self: start;
  align-self: center;
  padding: 5px;
  margin: 10px;
  width: 100px;
}
.todoCheckbox {
  grid-area: checkbox;
  justify-self: center;
  align-self: center;
  width: 20px;
}
.deleteTodo {
  grid-area: deleteTodo;
  border: none;
  background-color: inherit;
  color: #ff0000;
  width: 30px;
  height: 30px;
  align-self: center;
  justify-self: center;
}
.editTodo {
  grid-area: editTodo;
  border: none;
  background-color: inherit;
  color: #ff0000;
  width: 30px;
  height: 30px;
  align-self: center;
  justify-self: center;
}
</style>
