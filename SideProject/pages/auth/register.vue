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
      <div class="w-full h-screen bg-white rounded-xl flex justify-center items-center">   
        <div class="w-full h-full flex flex-col justify-center items-center">
            <div class="w-full h-24 flex justify-center items-center">
                <img class="w-24 h-24" src="~/assets/images/login.png" alt="logo" />
            </div>
            
            <FormKit
                type="form"
                v-if="!complete"
                id="registerForm"
                #default="{ value }"
                @submit="submitHandler"
                :submit-attrs="{
                  inputClass: 'w-72 h-12 bg-blue-500 text-white font-bold text-xl rounded-full mt-4',
                
                }"
            >
                <div class="w-full h-24 flex justify-center items-center">
                    <h1 class="text-3xl">Register</h1>
                </div>
                <div class="w-full h-24 flex justify-center items-center">
                    <FormKit label="Email" 
                        :input-class="{
                        'w-72 h-12  border-2 border-black outline-none text-xl font-thin': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="email" placeholder="Email..."
                    />
                </div>
                <div class="w-full h-24 flex justify-center items-center">
                    <FormKit label="Username"
                        :input-class="{
                        'w-72 h-12  border-2 border-black outline-none text-xl font-thin': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="username" placeholder="Username..."
                    />
                </div>
                <div class="w-full h-24 flex justify-center items-center">
                    <FormKit label="First Name"
                        :input-class="{
                        'w-72 h-12  border-2 border-black outline-none text-xl font-thin': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="first_name" placeholder="First name..."
                    />
                </div>
                <div class="w-full h-24 flex justify-center items-center">
                    <FormKit label="Last Name"
                        :input-class="{
                        'w-72 h-12  border-2 border-black outline-none text-xl font-thin': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="last_name" placeholder="Last name..."
                    />
                </div>
                <div class="w-full h-24 flex justify-center items-center">
                    <FormKit label="Password"
                        :input-class="{
                        'w-72 h-12  border-2 border-black outline-none text-xl font-thin': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl':true
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
      </div>
    </div>
</template>
