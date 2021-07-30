<template>
  <!-- v-bind: 親から渡す値を動的に変化させたい場合に用いる。記述は数式や値 -->
  <TheHeader
    :text="Math.floor(Math.random() * 10) % 2 === 0 ? 'even' : 'odd'"
  />
  <div v-if="!validationMessageList.length">{{ count }}</div>
  <div v-else v-for="message in validationMessageList" :key="message">
    {{ message }}
  </div>
  <BaseButton :disabled="hasMaxCount" @onClick="plusOne">+</BaseButton>

  <BaseButton :disabled="hasMinCount" @onClick="minusOne">-</BaseButton>

  <NumberInput v-model.numberOnly="inputCount" max="9999" min="0" />
  <BaseButton @onClick="insertCount">insert</BaseButton>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import BaseButton from "./components/BaseButton.vue";
import NumberInput from "./components/NumberInput.vue";

export default {
  components: {
    TheHeader,
    BaseButton,
    NumberInput,
  },
  data() {
    return {
      count: 0,
      inputCount: 0,
      isEditing: false,
    };
  },
  watch: {
    inputCount(value) {
      // if (value >= 9999) {
      //   this.inputCount = 9999;
      // }
      // // 入力値が0以下の場合、常にthis.inputCountを0で維持する
      // if (value <= 0) {
      //   this.inputCount = 0;
      // }
      this.isEditing = true;
    },
  },
  computed: {
    // 9999以上になったらtrueを返す
    hasMaxCount() {
      return this.count >= 9999;
    },
    // countが0以下になったら、trueを返す
    hasMinCount() {
      return this.count <= 0;
    },
    hasMaxInputCount() {
      return this.inputCount > 9999;
    },
    hasMinInputCount() {
      return this.inputCount < 0;
    },
    validationMessageList() {
      const validationList = [];

      if (this.isEditing) {
        validationList.push("編集中...");
      }

      if (this.hasMaxInputCount) {
        validationList.push("9999以上は入力できません。");
      }

      if (this.hasMinInputCount) {
        validationList.push("0以下は入力できません。");
      }

      return validationList;
    },
  },
  methods: {
    plusOne() {
      this.count++;
    },
    minusOne() {
      this.count--;
    },
    insertCount() {
      if (this.hasMaxInputCount || this.hasMinInputCount) return;
      this.count = this.inputCount;
      this.isEditing = false;
    },
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
