<template>
  <button @click="handleClick"><slot /></button>
</template>

<script>
export default {
  name: "BaseButton",
  methods: {
    handleClick() {
      this.$emit("onClick");
    },
  },
};
</script>
