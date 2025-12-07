<template>
  <q-card class="q-pa-xl items-center column" flat bordered elevation="0">
    <h3 class="text-primary">Welcome to BrandOne</h3>
    <q-form class="column q-gutter-md row justify-center" ref="signupForm" @submit="submitSingup">
      <h4 style="font-weight: 400">Sign Up</h4>

      <!--UserName Field-->
      <q-input
        standout="bg-primary text-white"
        v-model="username"
        label="UserName"
        style="width: 500px"
        :rules="[
          (val) => !!val || 'username is required',
          (val) => val.length >= 3 || 'username should be minimum 3 characters',
        ]"
      >
        <template v-slot:prepend>
          <q-icon name="person" />
        </template>
      </q-input>

      <!-- Email Field -->
      <q-input
        standout="bg-primary text-white"
        v-model="email"
        label="Email"
        style="width: 500px"
        :rules="[
          (val) => !!val || 'email is required',
          (val) => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(val) || 'Enter a valid email',
        ]"
      >
        <template v-slot:prepend>
          <q-icon name="email" />
        </template>
      </q-input>
      <!--Password Field-->
      <q-input
        standout="bg-primary text-white"
        v-model="password"
        :type="'password'"
        label="Password"
        style="width: 500px"
        :rules="[
          (val) => !!val || 'password is required',
          (val) => val.length >= 6 || 'password should be minimum 6 characters',
        ]"
      >
        <template v-slot:prepend>
          <q-icon name="lock" />
        </template>
      </q-input>

      <!--Confirm Password Field-->
      <q-input
        standout="bg-primary text-white"
        v-model="confirmpassword"
        :type="showPwd ? 'text' : 'password'"
        label="Confirm Password"
        style="width: 500px"
        :rules="[
        //   (val) => !!val || 'confirm password is required',
          (val) => val === password || 'password does not match',
        ]"
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

      <q-btn
        class="text-capitalize"
        label="Create account"
        color="primary"
        type="submit"
        style="width: 500px"
        rounded
        @click="movetologin('btn')"
      ></q-btn>
      <div class="row items-center q-my-md" style="width: 500px">
        <q-separator class="col"></q-separator>
        <span class="q-mx-sm">or</span>
        <q-separator class="col"></q-separator>
      </div>
      <div class="row">
        <span class="col-12">
          Already have an account?
          <span
            class="col-2"
            color="primary"
            style="cursor: pointer; color: #1976d2"
            @click="movetologin('span')"
            >Login</span
          >
        </span>
      </div>
    </q-form>
  </q-card>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['movetosignup'])
const username = ref('')
const password = ref('')
const confirmpassword = ref('')
const showPwd = ref(false)
const signupForm = ref(null)
// const rememberVal = ref(false)

function movetologin(type) {
  if (type === 'btn') {
    signupForm.value.validate().then((success) => {
      if (success) {
        emit('movetosignup', false)
      }
    })
  } else if (type === 'span') {
    emit('movetosignup', false)
  }
}
// function submitSingup(){}
// }
</script>
