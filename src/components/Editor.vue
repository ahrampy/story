<template>
  <div class="editor">
    <form class="form" v-on:submit="addStory">
      <input type="text" v-model="title" placeholder="title" />
      <input type="textarea" v-model="content" placeholder="start typing" />
      <button type="submit"></button>
    </form>
  </div>
</template>

<script>

export default {
  name: "Editor",
  data() {
    return {
      title: "",
      content: ""
    };
  },
  methods: {
    addStory(e) {
      e.preventDefault()
      const newStory = {
        id: 5,
        title: this.title,
        content: this.content,
        selected: false
      }
      this.$emit('addStory', newStory);
      this.title = '',
      this.content = ''
    }
  }
};
</script>

<style scoped>
.editor {
  background: darkolivegreen;
}

.form {
  display: flex;
  flex-direction: column;
}

input[type="text"] {
  height: 50px;
}

input[type="textarea"] {
  height: 200px;
}
</style>
