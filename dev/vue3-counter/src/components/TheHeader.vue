<template>
  <header>{{ text }}</header>
</template>

<script>
export default {
  name: "TheHeader",
  props: {
    text: {
      type: String,
      default: "",
    },
  },
};
</script>
