<script>
export default {
  name: "TextEditor",
  props: ["modelValue"],
  emits: ["update:modelValue"],
  data() {
    return {
      editing: false,
    };
  },
  methods: {
    enableEditing() {
      this.editing = true;
      this.$nextTick(function () {
        this.$refs.textInput.focus();
        document.execCommand("selectAll", null, false);
      });
    },
    endEditing() {
      this.editing = false;
    },
  },
};
</script>

<template>
  <span class="editor text">
    <input
      ref="textInput"
      v-if="editing"
      :value="modelValue"
      @change="$emit('update:modelValue', $event.target.value)"
      @blur="endEditing"
    />
    <span @click="enableEditing" v-else>{{ modelValue }}</span>
  </span>
</template>

<style scoped>
.editor:hover {
  outline: 1px solid gray;
}
</style>
