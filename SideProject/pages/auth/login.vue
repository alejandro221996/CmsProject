<!--Layout for login -->
<style>
.login {
  width: 100%;
  height: 100vh;
  background-color: #000;
  display: flex;
  justify-content: center;
  align-items: center;
}
.login__container {
  width: 400px;
  height: 500px;
  background-color: #fff;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.login__container__logo {
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.login__container__logo img {
  width: 100px;
  height: 100px;
}
.container_for_input {
  width: 100%;
  height: 400px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.container_for_input__title {
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.container_for_input__title h1 {
  font-size: 2rem;
  font-weight: 100;
}
.container_for_input__input {
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container_for_input__input input {
  width: 300px;
  height: 50px;
  border: none;
  border-bottom: 1px solid #000;
  outline: none;
  font-size: 1.2rem;
  font-weight: 100;
}
.container_for_input__button {
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
}


.container_for_input__button button {
  width: 300px;
  height: 50px;
  border: none;
  outline: none;
  background-color: #000;
  color: #fff;
  font-size: 1.2rem;
  font-weight: 100;
  cursor: pointer;
}
.container_for_input__button button:hover {
  background-color: #17b0eb;
}

.container_for_input__anchor a:hover {
  color: #17b0eb;
}

label{
  margin-left: -40px;
  cursor: pointer;
}
</style>

<script>
import { ref } from 'vue'
import { setErrors } from '@formkit/vue'
import { password } from '@formkit/inputs'
const completeLogin = ref(false)
const submitHandlerLogin = async (data) => {
      // We need to submit this as a multipart/form-data
      // to do this we use the FormData API.
      const body = new FormData()
      // We can append other data to our form data:
      body.append('password', data.password)
      body.append('username', data.username)
    // We'll perform a real upload to httpbin.org
    const res = await fetch('http://192.168.0.101:8000/api/token/', {
      method: 'POST',
      body: body,
    })
    //get data from response

    if (res.ok) {
      completeLogin.value = true
      const dataResponse = await res.json()
      localStorage.setItem('token', dataResponse.access)
      localStorage.setItem('refresh', dataResponse.refresh)
      window.location.href = '/home'
      
    } else {
      setErrors('loginForm', ['The server didn’t like our request.'])
    }
}

//Ocultar/mostrar password
export default {
    el: '#app',
    data(){
      return {
        type: "password",
        typeIcon: "hide-pass"
      };
    },
    props:{
      type: {type:String, default:"password"},
      typeIcon: {type:String, default:"hide-pass"}
    },
    methods:{
      showPassword() {
        if(this.type === 'password') {
          this.type = 'text'
          this.typeIcon = 'show-pass'
        } else {
          this.type = 'password'
          this.typeIcon = 'hide-pass'
        }
    }
	}
}

definePageMeta({
  layout: "auth-layout",
});
</script>
<template>
    <div class="login">
      <div class="login__container">   
        <div class="container_for_input">
            <div class="container_for_input__title">
              <h1 class="text-3xl text-black font-mono">Sign in</h1>
            </div>
            <div class="login__container__logo">
                <img class="w-32 h-32 " src="~/assets/images/login.png" alt="logo" />
            </div>
            <FormKit
                type="form"
                v-if="!completeLogin"
                id="loginForm"
                #default="{ value }"
                @submit="submitHandlerLogin"
                submit-label="Sign In"
                :submit-attrs="{
                  inputClass: 'w-72 h-12 bg-blue-500 text-white font-bold text-xl rounded-full mt-4',
                
                }"
            >
                <div class=" flex justify-center items-center">
                    <FormKit label="Username"
                        :input-class="{
                        'w-72 h-12 border-2 border-black outline-none text-xl font-thin px-2 rounded-xl pb-6 pt-6': true,
                        }"
                        :messages-class="{
                        'text-red-500': true,
                        }"
                        :label-class="{
                            'text-xl px-14':true
                        }"
                        validation="required"
                        validation-visibility="dirty"
                        type="text" name="username" placeholder="Username..."
                    />
                </div>
                <div class=" flex justify-center items-center" id="app">
                      <FormKit label="Password"
                          :input-class="{
                          'w-72 h-12 border-2 border-black outline-none text-xl font-thin px-2 rounded-xl pb-6 pt-6': true,
                          }"
                          :messages-class="{
                          'text-red-500 fixed': true,
                          }"
                          :label-class="{
                          'text-xl px-14':true
                          }"
                          :type="this.type"
                          validation="required"
                          validation-visibility="dirty"
                          name="password" placeholder="Password..."
                      />
                      <div class="w-1 h-24 flex items-center ">
                        <label 
                            type="button" 
                            @click="showPassword" 
                            :class="{
                              'w-8 h-12 pt-2 outline-none text-xl font-thin mt-7': true,
                              }">
                          <div v-if="this.typeIcon === 'show-pass'">
                            <svg :class="this.typeIcon" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
                              <path stroke-linecap="round" stroke-linejoin="round" d="M2.036 12.322a1.012 1.012 0 010-.639C3.423 7.51 7.36 4.5 12 4.5c4.638 0 8.573 3.007 9.963 7.178.07.207.07.431 0 .639C20.577 16.49 16.64 19.5 12 19.5c-4.638 0-8.573-3.007-9.963-7.178z"></path>
                              <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"></path>
                            </svg>
                          </div>
                          <div v-else>
                            <svg fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
                              <path stroke-linecap="round" stroke-linejoin="round" d="M3.98 8.223A10.477 10.477 0 001.934 12C3.226 16.338 7.244 19.5 12 19.5c.993 0 1.953-.138 2.863-.395M6.228 6.228A10.45 10.45 0 0112 4.5c4.756 0 8.773 3.162 10.065 7.498a10.523 10.523 0 01-4.293 5.774M6.228 6.228L3 3m3.228 3.228l3.65 3.65m7.894 7.894L21 21m-3.228-3.228l-3.65-3.65m0 0a3 3 0 10-4.243-4.243m4.242 4.242L9.88 9.88"></path>
                            </svg>
                          </div>
                        
                        </label>
                      </div>
                </div>
            </FormKit>
            <div v-else class="completeLogin">User was created successfully 👍</div>
            <div class="flex h-24 w-3/4 justify-center items-center mt-4 text-slate-400">
                DON'T HAVE AN ACCOUNT? <NuxtLink class="items-center hover:text-sky-600 ml-2 text-slate-900" to="/auth/register"> SIGN UP</NuxtLink>
            </div>
        </div>
      </div>
    </div>
</template>
