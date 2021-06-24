<template>
  <div class="Item">
    <p v-for="post in posts" :key="post.id">{{ post.id }} {{ post.title }}</p>
    <p>{{ test1 }}</p>
    <p>{{ test3 }}</p>
  </div>
</template>

<script>
export default {
  name: "ToDoItem",
  props: {
    test1: String,
    test2: String,
    test3: String,
  },
  data() {
    return {
      posts: [
        { id: 1, title: "My journey with Vue" },
        { id: 2, title: "Blogging with Vue" },
        { id: 3, title: "Why Vue is so fun" },
      ],
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
