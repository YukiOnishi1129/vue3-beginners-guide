<template>
  <input type="number" :value="modelValue" @input="emitValue" />
</template>

<script>
export default {
  name: "NumberInput",
  emits: ["update:modelValue"],
  props: {
    modelValue: {
      type: Number,
      default: 0,
    },
    modelModifiers: {
      default: () => ({}),
    },
  },
  methods: {
    emitValue({ target: { value } }) {
      if (this.modelModifiers.numberOnly && value === "") {
        value = 0;
      }

      this.$emit("update:modelValue", Number(value));
    },
  },
};
</script>
