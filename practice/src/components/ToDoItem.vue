<template>
  <div class="Item">
    <p v-for="post in posts" :key="post.id">{{ post.id }} {{ post.title }}</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      posts: [
        { id: 1, title: 'My journey with Vue' },
        { id: 2, title: 'Blogging with Vue' },
        { id: 3, title: 'Why Vue is so fun' },
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
