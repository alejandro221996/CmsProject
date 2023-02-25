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
</style>
<script>
import { ref } from 'vue'
import { setErrors } from '@formkit/vue'
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
definePageMeta({
  layout: "auth-layout",
});
</script>
<template>
    <div class="login">
      <div class="login__container">   
        <div class="container_for_input">
            <div class="login__container__logo">
                <img src="~/assets/images/login.png" alt="logo" />
            </div>
            <div class="container_for_input__title">
                <h1>Sign in</h1>
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
                <details>
                  <pre class="text-red-500">{{ value }}</pre>

                </details>
            </FormKit>
            <div v-else class="completeLogin">User was created successfully 👍</div>
            <div class="flex h-24 w-3/4 justify-center items-center mt-4 text-slate-400">
                DON'T HAVE AN ACCOUNT? <NuxtLink class="items-center hover:text-sky-600 ml-2 text-slate-900" to="auth/register"> SIGN UP</NuxtLink>
            </div>
        </div>
      </div>
    </div>
</template>
