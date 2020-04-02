<template>
  <div id="app">
    <Nav />
    <Editor />
    <Stories v-bind:stories = "stories" v-on:delete-story="deleteStory"/>
  </div>
</template>

<script>
import Nav from "./components/Nav"
import Editor from "./components/Editor"
import Stories from "./components/Stories.vue";

export default {
  name: "App",
  components: {
    Nav,
    Editor,
    Stories
  },
  data() {
    return {
      stories: [
        {
          id: 1,
          title: "the first",
          content: "once upon a time, the end",
          selected: false
        },
        {
          id: 2,
          title: "the second",
          content: "and then it was as it had always been before",
          selected: false
        },
        {
          id: 3,
          title: "the third",
          content: "after a while things were pretty okay",
          selected: true
        }
      ]
    }
  },
  methods: {
    deleteStory(id) {
      this.stories = this.stories.filter(story => story.id !== id);
    }
  }
};
</script>

<style>
@import "reset.css";

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
