<template>
  <div id="app">
    <Editor v-on:addStory="addStory" />
    <Stories v-bind:stories="stories" v-on:delete-story="deleteStory" />
  </div>
</template>

<script>
import Editor from "../components/Editor";
import Stories from "../components/Stories.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Editor,
    Stories
  },
  data() {
    return {
      stories: []
    };
  },
  methods: {
    deleteStory(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(
          () => (this.stories = this.stories.filter(story => story.id !== id))
        )
        .catch(err => console.log(err));
    },
    addStory(newStory) {
      const { title, content } = newStory;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          content
        })
        .then(res => (this.stories = [...this.stories, res.data]))
        .catch(err => console.log(err));
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=10")
      .then(res => (this.stories = res.data.map(todo => {
        todo.selected = false;
        return todo
      })))
      .catch(err => console.log(err));
  }
};
</script>

<style>
@import "../reset.css";

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #333;
}
</style>
