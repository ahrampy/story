<template>
  <div id="editor">
    <editor-menu-bar :editor="editor" v-slot="{ commands, isActive }">
      <button :class="{ 'is-active': isActive.bold() }" @click="commands.bold">
        Bold
      </button>
    </editor-menu-bar>
    <editor-content :editor="editor" />
  </div>
</template>

<script>
import { Editor, EditorContent, EditorMenuBar } from "tiptap";
import { Bold, Italic, Strike, Underline } from "tiptap-extensions";

export default {
  components: {
    EditorMenuBar,
    EditorContent,
  },
  data() {
    return {
      editor: new Editor({
        extensions: [new Bold(), new Italic(), new Strike(), new Underline()],
        content: `
          <h1>Yay Headlines!</h1>
          <p>All these <strong>cool tags</strong> are working now.</p>
        `,
      }),
    };
  },
  beforeDestroy() {
    this.editor.destroy();
  },
};
</script>

<style scoped>
  #editor {
    
  }
</style>
