<template>
  <div v-if="editor" class="editor-container">
    <div class="flex justify-between gap-x-5">
      <!-- Headings -->
      <div class="flex gap-x-5 cursor-pointer items-center">
        <button type="button" @click="handleHeader(1)">H1</button>
        <button type="button" @click="handleHeader(2)">H2</button>
        <button type="button" @click="handleHeader(3)">H3</button>
        <button type="button" @click="handleHeader(4)">H4</button>
      </div>

      <!--font style-->
      <div class="flex gap-x-5 cursor-pointer items-center">
        <button type="button" @click="handleBold">Bold</button>
        <button type="button" @click="handleItalics">Italic</button>
        <button type="button" @click="handleStrike">Strike</button>
      </div>

      <!-- Lists and Alignment -->
      <div class="flex gap-x-5 cursor-pointer items-center">
        <button type="button" @click="handleBulletList">Bullet List</button>
        <button type="button" @click="handleOrderedList">Ordered List</button>
      </div>
    </div>
    <editor-content :editor="editor" class="prose max-w-full" />
  </div>
</template>

<script setup>
import { useEditor, EditorContent } from "@tiptap/vue-3";
import StarterKit from "@tiptap/starter-kit";

const editor = useEditor({
  content: "",
  extensions: [StarterKit],
});

const handleHeader = (number) => {
  editor.value?.chain()?.focus()?.toggleHeading({ level: number }).run();
};

const handleBold = () => {
  editor.value?.chain()?.focus()?.toggleBold().run();
};

const handleItalics = () => {
  editor.value?.chain()?.focus()?.toggleItalic().run();
};

const handleStrike = () => {
  editor.value?.chain()?.focus()?.toggleStrike().run();
};

const handleBulletList = () => {
  editor.value?.chain()?.focus()?.toggleBulletList().run();
};

const handleOrderedList = () => {
  editor.value?.chain()?.focus()?.toggleOrderedList().run();
};
</script>

<style>
.editor-container {
  border: 1px solid #e0e0e0;
  min-height: 150px;
  width: 50%;
  padding: 5px;
  border-radius: 6px;
  margin: auto;
}
.editor-container .toolbar {
  border-bottom: 1px solid #f6f8fa;
  background-color: #f6f8fa;
}

.editor-content {
  outline: none;
}

.ProseMirrorWrapper {
  @apply w-full  rounded-md  border  outline-none  border-slate-200  bg-white  text-sm  min-h-[32rem];
}
</style>
