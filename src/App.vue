<script setup>
  import {ref} from "vue";
  import Modal from "@/components/Modal/Modal.vue";
  import MainButton from "@/components/MainButton/MainButton.vue";

  const modalStatus = ref(false);

  const toggleModal = () => {
    modalStatus.value = !modalStatus.value;
  }
</script>

<template>
  <div class="container">
    <MainButton title="Open" @click="toggleModal"/>
    <Modal v-if="modalStatus" @closeModal="toggleModal"/>
  </div>
</template>

<style scoped>
  .container {
    width: 100vw;
    height: 100vh;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
