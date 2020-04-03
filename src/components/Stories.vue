<template>
  <div>
    <h1>Stories</h1>

    <div v-for="story in stories" v-bind:key="story.id">
      <Story
        v-bind:story="story"
        v-on:delete-story="$emit('delete-story', story.id)"
        v-on:selected-story="$emit('selected-story', story.id)"
      />
    </div>
  </div>
</template>

<script>
import Story from "./Story"

export default {
  name: "Stories",
  components: {
    Story
  },
  props: ["stories"]
};
</script>

<style scoped>
</style>