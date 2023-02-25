<script setup>
import { ref } from 'vue'
import { setErrors } from '@formkit/vue'
const complete = ref(false)

const submitHandler = async (data) => {
    // We need to submit this as a multipart/form-data
    // to do this we use the FormData API.
    console.log("Entrando a submitHandler")
    const body = new FormData()
    // We can append other data to our form data:
    body.append('email', data.email)
    body.append('password', data.password)
    body.append('first_name', data.first_name)
    body.append('last_name', data.last_name)
    body.append('username', data.username)
  // We'll perform a real upload to httpbin.org
  const res = await fetch('http://192.168.0.101:8000/api/accounts/users/', {
    method: 'POST',
    body: body,
  })

  if (res.ok) {
    complete.value = true
  } else {
    setErrors('registerForm', ['The server didn’t like our request.'])
  }
}
definePageMeta({
  layout: "auth-layout",
});
</script>
<template>
    <div class="h-screen w-full bg-black flex justify-center items-center">     
            <FormKit
                type="form"
                v-if="!complete"
                id="registerForm"
                #default="{ value }"
                @submit="submitHandler"
                :submit-attrs="{
                    inputClass: 'w-72 h-12 bg-blue-500 text-white font-bold text-xl rounded-full mt-4',
                
                }"
                :wrapper-class="{
                    'bg-white': true,
                    'i-will-not': false
                }"
                :form-class="{
                    'bg-white px-28 rounded-xl pb-6 pt-6': true,
                }"       
            >
                <div class=" flex justify-center items-center">
                    <h1 class="text-3xl text-black font-mono">Register</h1>
                </div>
                <div class=" flex justify-center items-center">
                    <img class="w-32 h-32 " src="~/assets/images/login.png" alt="logo" />
                </div>
                <div class=" flex justify-center items-center">
                    <FormKit label="Email" 
                        :input-class="{
                        ' text-white border-2 rounded-xl border-black outline-none text-xl font-thin p-2 mb-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl p-4':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="email" placeholder="Email..."
                    />
                </div>
                <div class=" flex justify-center items-center">
                    <FormKit label="Username"
                        :input-class="{
                        'text-white border-2 rounded-xl border-black outline-none text-xl font-thin p-2  mb-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl p-4':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="username" placeholder="Username..."
                    />
                </div>
                <div class="flex justify-center items-center">
                    <FormKit label="First Name"
                        :input-class="{
                        'text-white border-2 rounded-xl border-black outline-none text-xl font-thin p-2  mb-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl p-4':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="first_name" placeholder="First name..."
                    />
                </div>
                <div class=" flex justify-center items-center">
                    <FormKit label="Last Name"
                        :input-class="{
                        'text-white border-2 rounded-xl border-black outline-none text-xl font-thin p-2  mb-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl p-4':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="last_name" placeholder="Last name..."
                    />
                </div>
                <div class="w-full h-24 flex justify-center items-center">
                    <FormKit label="Password"
                        :input-class="{
                        'text-white border-2 rounded-xl border-black outline-none text-xl font-thin p-2  mb-2': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl p-4':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="password" name="password" placeholder="Password..."
                    />
                </div>
            </FormKit>
            <div v-else class="flex justify-center items-center flex-col    ">
                
                <div class="w-full h-24 flex justify-center items-center ">
                    <h1 class="text-3xl">User was created successfully 👍</h1>
                </div>
                <div class="w-full  flex justify-center items-center">
                    <NuxtLink to="/" class="text-3xl items-center hover:text-emerald-500 ">Login</NuxtLink>
                </div>
            </div>
    </div>
</template>
