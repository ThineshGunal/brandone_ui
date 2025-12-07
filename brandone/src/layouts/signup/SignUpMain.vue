<template>
  <q-page class="row no-wrap">
    <SignUpLeft class="col-6"></SignUpLeft>
    <SignInForm class="col-6" @movetosignup="movetosignup" v-if="!isSignUp"></SignInForm>
    <SignUpForm class="col-6" @movetosignup="movetosignup" v-if="isSignUp"></SignUpForm>
  </q-page>
</template>
<script setup>
import SignUpLeft from './SignUpLeft.vue'
import SignInForm from './SignInForm.vue'
import SignUpForm from './SignUpForm.vue'
import { ref } from 'vue'
const isSignUp = ref(false)
function movetosignup(value) {
  isSignUp.value = value
}
</script>
