<template>
  <div class="story" v-on:click="select" v-bind:class="{'is-current':story.selected}">
    <h1>{{story.title}}</h1>
    <button class="delete" v-on:click="$emit('delete-story', story.id)">x</button>
  </div>
</template>

<script>
export default {
  name: "Story",
  props: ["story"],
  methods: {
    select() {
      this.story.selected = true;
    }
  }
}
</script>

<style scoped>
  .story {
    display: flex;
    justify-content: space-between;
    background: brown;
  }

  .story:hover {
    background: burlywood;
  }

  .is-current {
    background: cornsilk;
  }

  .delete {
    width: 20px;
  }
</style>