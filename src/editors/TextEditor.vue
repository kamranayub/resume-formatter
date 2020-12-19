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
      ref="textValue"
      @click="enableEditing"
      @blur="endEditing"
      contenteditable="true"
      >{{ modelValue }}</span
    >
  </span>
</template>

<style scoped>
.editor:hover {
  outline: 1px solid gray;
}
</style>
