<script>
export default {
  name: 'TextEditor',
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
    },
    endEditing() {
      this.editing = false;
    },
  },
};
</script>

<template>
  <input
    v-if="editing"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    @blur="endEditing"
  />
  <span @click="enableEditing" v-else>{{ modelValue }}</span>
</template>
