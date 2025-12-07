<template>
  <q-card class="q-pa-xl items-center column" flat bordered elevation="0">
    <h3 class="text-primary">Welcome to BrandOne</h3>
    <q-form class="column q-gutter-md row justify-center">
      <h4 style="font-weight: 400">Sign in</h4>
      <q-input standout="bg-primary text-white" v-model="email" label="Email" style="width: 500px">
        <template v-slot:prepend>
          <q-icon name="email" />
        </template>
      </q-input>
      <q-input
        standout="bg-primary text-white"
        v-model="password"
        :type="showPwd ? 'text' : 'password'"
        label="Password"
        style="width: 500px"
      >
        <template v-slot:prepend>
          <q-icon name="lock" />
        </template>
        <template v-slot:append>
          <q-icon
            :name="showPwd ? 'visibility' : 'visibility_off'"
            class="cursor-pointer"
            @click="showPwd = !showPwd"
          />
        </template>
      </q-input>
      <div class="row no-wrap">
        <q-checkbox v-model="rememberVal" class="col-6">Remember me</q-checkbox>
        <span
          class="col-6 q-pt-md row justify-end text-secondary"
          style="cursor: pointer"
          color="primary"
          >Forgot Password?</span
        >
      </div>
      <q-btn
        class="text-capitalize"
        label="Login"
        color="primary"
        type="submit"
        style="width: 500px"
        rounded
      ></q-btn>
      <div class="row items-center q-my-md" style="width: 500px">
        <q-separator class="col"></q-separator>
        <span class="q-mx-sm">or</span>
        <q-separator class="col"></q-separator>
      </div>
      <div class="row">
        <span class="col-12">
          Don't have an account?
          <span
            class="col-2"
            color="primary"
            style="cursor: pointer; color: #1976d2"
            @click="movetosignup()"
            >Sign Up</span
          >
        </span>
      </div>
    </q-form>
  </q-card>
</template>

<script setup>
// export default {
//   data() {
// return {
import { ref } from 'vue'

const emit = defineEmits(['movetosignup'])
// const username =ref('');
const password = ref('')
const showPwd = ref(false)
const rememberVal = ref(false)

// password: '',
// showPwd: false,
// rememberVal: false,
//   }
// },
// methods:{
function movetosignup() {
  emit('movetosignup', true)
}
//   }
// }
</script>
