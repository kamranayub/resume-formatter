<script>
export default {
  name: "TextEditor",
  props: ["modelValue"],
  emits: ["update:modelValue"],
  methods: {
    enableEditing() {
      document.execCommand("selectAll", null, false);
    },
    endEditing() {
      const html = this.$refs.textValue.innerHTML;
      this.$emit("update:modelValue", html);
    },
  },
};
</script>

<template>
  <span class="editor text">
    <span
      class="editor-inner"
      ref="textValue"
      @click="enableEditing"
      @blur="endEditing"
      contenteditable="true"
      >{{ modelValue }}</span
    >
  </span>
</template>

<style scoped>
.editor-inner {
  display: inline-block;
  margin: 1px;
}

.editor:hover .editor-inner {
  box-shadow: 0 0 3px gray;
  border-radius: 3px;
  background: var(--color-highlight);
}
</style>
