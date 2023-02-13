<script setup>
  import {defineProps} from "vue";

  const {title, type} = defineProps(["title", "type"]);
</script>

<template>
  <button :type="type" class="main_button">{{ title }}</button>
</template>

<style scoped>
  .main_button {
    padding: 13px 24px;
    border-radius: 35px;
    background-color: #C24DFE;
    font-size: 12px;
    font-weight: 700;
    color: #fff;
    border: none;
    cursor: pointer;
  }

  .main_button:hover {
    background-color: #b340ee;
  }

  .main_button:active {
    background-color: #a133d9;
  }
</style>