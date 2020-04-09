<template>
  <div class="editor">
    <editor-menu-bar :editor="editor" v-slot="{ commands, isActive }">
      <div class="menubar">
        <button
          class="menubar_button"
          :class="{ 'is-active': isActive.bold() }"
          @click="commands.bold"
        >
          <img src="../assets/icons/bold.png" />
        </button>

        <button
          class="menubar_button"
          :class="{ 'is-active': isActive.italic() }"
          @click="commands.italic"
        >
          <img src="../assets/icons/italic.png" />
        </button>

        <button
          class="menubar_button"
          :class="{ 'is-active': isActive.underline() }"
          @click="commands.underline"
        >
          <img src="../assets/icons/underline.png" />
        </button>

        <button
          class="menubar_button"
          :class="{ 'is-active': isActive.strike() }"
          @click="commands.strike"
        >
          <img src="../assets/icons/strike.png" />
        </button>

        <!-- <button
          class="menubar_button"
          :class="{ 'is-active': isActive.code() }"
          @click="commands.code"
        >
          <icon name="code" />
        </button> -->

        <!-- <button
          class="menubar_button"
          :class="{ 'is-active': isActive.paragraph() }"
          @click="commands.paragraph"
        >
          <icon name="paragraph" />
        </button> -->

        <!-- <button
          class="menubar_button"
          :class="{ 'is-active': isActive.heading({ level: 1 }) }"
          @click="commands.heading({ level: 1 })"
        >
          H1
        </button> -->

        <!-- <button
          class="menubar_button"
          :class="{ 'is-active': isActive.heading({ level: 2 }) }"
          @click="commands.heading({ level: 2 })"
        >
          H2
        </button>

        <button
          class="menubar_button"
          :class="{ 'is-active': isActive.heading({ level: 3 }) }"
          @click="commands.heading({ level: 3 })"
        >
          H3
        </button> -->

        <!-- <button
          class="menubar_button"
          :class="{ 'is-active': isActive.blockquote() }"
          @click="commands.blockquote"
        >
          <icon name="quote" />
        </button> -->

        <!-- <button
          class="menubar_button"
          @click="commands.undo"
        >
          <icon name="undo" />
        </button>

        <button
          class="menubar_button"
          @click="commands.redo"
        >
          <icon name="redo" />
        </button> -->
      </div>
    </editor-menu-bar>

    <editor-content class="editor__content" :editor="editor" />
  </div>
</template>

<script>
import { Editor, EditorContent, EditorMenuBar } from "tiptap";
import {
  Heading,
  Bold,
  Italic,
  Link,
  Strike,
  Underline,
} from "tiptap-extensions";
export default {
  components: {
    EditorContent,
    EditorMenuBar,
  },
  data() {
    return {
      editor: new Editor({
        extensions: [
          new Heading({ levels: [1, 2, 3] }),
          new Link(),
          new Bold(),
          new Italic(),
          new Strike(),
          new Underline(),
        ],
        content: `start typing...`,
      }),
    };
  },
  beforeDestroy() {
    this.editor.destroy();
  },
};
</script>

<style scoped>
.editor {
  height: 100vh;
  margin: 1%;
}

.menubar_button {
  position: relative;
  display: inline-block;
  vertical-align: middle;
  object-fit: contain;
  width: 2.4rem;
  height: 2rem;
  margin: 0 0.3rem;
  /* top: -0.05rem; */
  border: currentColor;
  border-radius: 2px;
}

.is-active {
  background-color: rgb(232, 232, 232);
}
.menubar_button:hover {
  background-color: rgb(240, 240, 240);
}

.menubar_button > img {
  height: 80%;
}
</style>
