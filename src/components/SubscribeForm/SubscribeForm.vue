<script setup>
  import {ref} from "vue";
  import MainButton from "@/components/MainButton/MainButton.vue";

  const email = ref("");
  const validEmail = ref(false);
  const policyStatus = ref(false);
  const errorMessage = ref("");
  const subscribeStatus = ref(false);

  const subscribeEmail = (value) => {
    if (!emailValidation(value)) {
      validEmail.value = false;
      errorMessage.value = "Invalid e-mail address";
      return;
    }

    if (!policyStatus.value) {
      errorMessage.value = "You must accept the privacy policy before continuing";
      return;
    }

    if (!saveToLocalStorage(value)) {
      subscribeStatus.value = false;
      errorMessage.value = "You have already subscribed to the newsletter";
      validEmail.value = false;
      return;
    }
    subscribeStatus.value = true;
    errorMessage.value = "You have successfully subscribed to the newsletter";
  }

  const emailValidation = (value) => {
    const regex = /^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/;

    if (value.trim() === "" || !regex.test(value)) {
      return false;
    }
    validEmail.value = true;
    return true;
  }

  const saveToLocalStorage = (value) => {
    let savedData = localStorage.getItem("email");
    if (savedData !== value) {
      localStorage.setItem("email", value);
      return true;
    } else {
      return false;
    }
  }
</script>

<template>
  <form class="form_container">
    <div class="form_input_container">
      <label class="form_label" for="email">E-mail address</label>
      <input
          class="form_input"
          type="text" id="email"
          v-model="email"
          :style="errorMessage && !validEmail ? {borderColor: '#fc7777'} : null"
      />
      <p class="form_error" v-if="errorMessage" :style="errorMessage && subscribeStatus ? {color: '#4ad952'} : {color: '#fc7777'}">{{ errorMessage }}</p>
    </div>
    <MainButton title="Subscribe!" type="subscribe" @click.prevent="subscribeEmail(email)"/>
    <label class="form_checkbox_container">
      I'm agree with privacy policy
      <input type="checkbox" v-model="policyStatus"/>
      <div class="form_checkmark"><div></div></div>
    </label>
  </form>
</template>

<style scoped>
  .form_container {
    max-width: 302px;
  }

  .form_input_container {
    margin-bottom: 16px;
  }

  .form_label {
    display: block;
    margin-bottom: 8px;
    font-weight: 700;
    color: #828688;
    line-height: 14px;
  }

  .form_input {
    border-radius: 6px;
    border: 1px solid #D5D7D7;
    padding: 0 11px;
    width: 100%;
    height: 40px;
  }

  .form_error {
    position: absolute;
    left: 11px;
    /*color: #fc7777;*/
    font-size: 12px;
  }

  .form_checkbox_container {
    display: block;
    position: relative;
    padding-left: 24px;
    cursor: pointer;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    margin-top: 16px;
    font-weight: 500;
    font-family: RobotoMedium, sans-serif;
  }

  .form_checkbox_container input {
    position: absolute;
    opacity: 0;
    cursor: pointer;
    height: 0;
    width: 0;
  }
  
  .form_checkmark {
    position: absolute;
    top: 2px;
    left: 0;
    height: 16px;
    width: 16px;
    padding: 2px;
    border: 2px solid #C24DFE;
    border-radius: 6px;
  }
  
  .form_checkbox_container input:checked ~ .form_checkmark div {
    width: 100%;
    height: 100%;
    background-color: #C24DFE;
    border-radius: 2px;
  }
</style>