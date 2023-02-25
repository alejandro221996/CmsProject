<script setup>
import { ref } from 'vue'
import { setErrors } from '@formkit/vue'
const complete = ref(false)
const generatePassword = () => {
  var length = 8,
      charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789",
      retVal = "";
  for (var i = 0, n = charset.length; i < length; ++i) {
      retVal += charset.charAt(Math.floor(Math.random() * n));
  }
  return retVal;
}
const submitRecHandler = async (data) => {
    // We need to submit this as a multipart/form-data
    // to do this we use the FormData API.
    const tempPassword = generatePassword()
    console.log("Entrando a submitRecHandler")
    const body = new FormData()
    // We can append other data to our form data:
    body.append('email', data.email)
    body.append('password', tempPassword)
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
    layout: "custom",
});
</script>
<template>
    <div>
        <h1 class="text-3xl mb-4 font-mono font-bold">Create a new user</h1>
        <section class="border-2 border-gray-300 rounded-lg p-10">
            <h1 class="text-2xl mb-10 font-mono font-semibold">Personal Information</h1>
            <FormKit
                type="form"
                v-if="!complete"
                id="registerForm"
                #default="{ value }"
                @submit="submitRecHandler"
                :submit-attrs="{
                  inputClass: 'w-72 h-12 bg-blue-500 text-white font-bold text-xl rounded-full mt-4',
                
                }"
                
            >
                <FormKit label="Email" 
                        :input-class="{
                        'w-96 h-12  border-2 border-gray-400 rounded-full p-4 text-xl font-thin mt-2': true,
                        }"
                        :messages-class="{
                        'text-red-500 p-4': true,
                        }"
                        :label-class="{
                            'text-xl p-4 font-mono':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="email" placeholder="Email..."
                />
                <FormKit label="Username" 
                        outer-class="mt-4"
                        :input-class="{
                            'w-96 h-12  border-2 border-gray-400 rounded-full p-4 text-xl font-thin mt-2': true,
                        }"
                        :messages-class="{
                            'text-red-500 p-4': true,
                        }"
                        :label-class="{
                            'text-xl p-4 font-mono':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="username" placeholder="Username..."
                />
                <FormKit label="First Name" 
                        outer-class="mt-4"
                        :input-class="{
                        'w-96 h-12  border-2 border-gray-400 rounded-full p-4 text-xl font-thin mt-2': true,
                        }"
                        :messages-class="{
                        'text-red-500 p-4': true,
                        }"
                        :label-class="{
                            'text-xl p-4 font-mono':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="first_name" placeholder="First Name..."
                />
                <FormKit label="Last Name" 
                        outer-class="mt-4 mb-4"
                        :input-class="{
                        'w-96 h-12  border-2 border-gray-400 rounded-full p-4 text-xl font-thin mt-2': true,
                        }"
                        :messages-class="{
                        'text-red-500 p-4': true,
                        }"
                        :label-class="{
                            'text-xl p-4 font-mono':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="last_name" placeholder="Last Name..."
                />
            </FormKit>
            <div v-else class="flex justify-center items-center">
                <div class="w-full h-24 flex justify-center items-center ">
                    <h1 class="text-3xl">User was created successfully 👍</h1>
                </div>
            </div>
        </section>
    
    </div>
</template>
