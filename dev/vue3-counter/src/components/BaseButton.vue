<template>
  <button @click="handleClick">ボタン</button>
</template>

<script>
export default {
  name: "BaseButton",
  methods: {
    handleClick() {
      alert("Hello world!");
    },
  },
};
</script>
