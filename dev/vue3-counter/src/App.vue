<template>
  <!-- v-bind: 親から渡す値を動的に変化させたい場合に用いる。記述は数式や値 -->
  <TheHeader
    :text="Math.floor(Math.random() * 10) % 2 === 0 ? 'even' : 'odd'"
  />
  <BaseButton />
  <BaseButton />
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import BaseButton from "./components/BaseButton.vue";

export default {
  components: {
    TheHeader,
    BaseButton,
  },
};

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/master/active-rfcs/0040-script-setup.md
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
