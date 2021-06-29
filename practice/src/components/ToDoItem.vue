<template>
  <div class="Item">
    <input
      type="checkbox"
      @click="$emit('onToggle')"
      :checked="todo.completed"
      class="todoCheckbox"
    />
    <input
      v-if="isEditing"
      v-model="editedValue"
      class="inputTodo"
      type="text"
      ref="editedValue"
      @keyup.enter="
        $emit('onEdit', todo.id, editedValue);
        isEditing = false;
      "
    />
    <p
      v-else-if="!isEditing"
      @click="$emit('onToggle')"
      :class="todo.completed ? 'completed' : null"
    >
      {{ todo.title }}
    </p>
    <button
      v-if="isEditing"
      @click="
        $emit('onEdit', todo.id, editedValue);
        isEditing = false;
      "
      class="btn saveEdited"
    >
      &#x1F4BE;
    </button>
    <button
      v-if="!isEditing"
      class="btn editTodo"
      @click="
        isEditing = !isEditing;
        testMet(todo.id);
      "
    >
      &#9997;
    </button>
    <button class="btn deleteTodo" @click="$emit('onDelete')">&#x274C;</button>
  </div>
</template>

<script>
export default {
  name: "ToDoItem",
  props: {
    todo: Object,
  },
  data() {
    return {
      isEditing: false,
      editedValue: this.todo.title,
    };
  },
  methods: {
    testMet() {
      this.$nextTick(() => this.$refs.editedValue.focus());
    },
  },
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
  margin: 5px;
  width: 100px;
}
.todoCheckbox {
  grid-area: checkbox;
  justify-self: center;
  align-self: center;
  width: 20px;
}
.btn {
  border: none;
  background-color: inherit;
  /* width: 15px; */
  /* height: 15px; */
  align-self: center;
}
.deleteTodo {
  grid-area: deleteTodo;
  color: #ff0000;
}
.editTodo {
  justify-self: end;
  grid-area: editTodo;
}
.saveEdited {
  justify-self: end;
  grid-area: editTodo;
}
.inputTodo {
  border: none;
  padding: 5px;
  margin: 5px;
  width: 80%;
  outline: none;
}
</style>
