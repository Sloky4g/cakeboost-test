<script setup>
  import {defineEmits} from "vue";
  import SubscribeForm from "@/components/SubscribeForm/SubscribeForm.vue";

  const emit = defineEmits(["closeModal"]);

  const closeModal = () => {
    emit("closeModal");
  }
</script>

<template>
  <div class="overlay">
    <div class="modal">
      <div class="modal_bg">
        <img src="/img/modal/modal-bg.png" alt="modal-bg">
      </div>
      <button class="close_button" @click="closeModal">
        <img src="/img/modal/close-icon.svg" alt="close-icon"/>
      </button>
      <h2 class="modal_title">10%<span>off</span></h2>
      <p class="modal_subtitle">your first order</p>
      <div class="modal_delimiter"/>
      <p class="modal_text">Subscribe to receive 10% off promo code plus exclusive offers and deals</p>
      <SubscribeForm/>
    </div>
  </div>
</template>

<style scoped>
  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 10;
    background-color: rgba(0, 0, 0, .2);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal {
    width: 864px;
    margin: 0 auto;
    padding: 40px 32px;
    background-color: #fff;
    position: relative;
    border-radius: 8px;
    overflow: hidden;
  }

  .modal_bg {
    position: absolute;
    top: 0;
    right: 0;
    width: auto;
    height: 100%;
  }

  .modal_bg img {
    width: 100%;
    height: 100%;
  }

  .close_button {
    position: absolute;
    top: 7px;
    right: 7px;
    z-index: 20;
    background-color: #fff;
    border-radius: 50%;
    padding: 5px;
    border: none;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
  }
  
  .close_button:hover {
    background-color: #eee;
  }

  .modal_title {
    max-width: 373px;
    font-weight: 700;
    font-size: 104px;
    line-height: 104px;
    color: #2F3639;
    margin-bottom: 16px;
  }

  .modal_title span {
    font-size: 24px;
    line-height: 24px;
    font-weight: 700;
  }

  .modal_subtitle {
    max-width: 373px;
    font-weight: 700;
    font-size: 24px;
    line-height: 24px;
    color: #828688;
    margin-bottom: 26px;
  }

  .modal_delimiter {
    width: 67px;
    height: 2px;
    background-color: #C24DFE;
    margin-bottom: 26px;
  }

  .modal_text {
    max-width: 373px;
    color: #595E61;
    margin-bottom: 40px;
    line-height: 16px;
  }
</style>