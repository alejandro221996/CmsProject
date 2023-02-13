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
</style>
<template>
  <div>
    <div class="login">
    
      <div class="login__container">
       
        <div class="container_for_input">
            <div class="login__container__logo">
                <img src="~/assets/images/login.png" alt="logo" />
            </div>
            <div class="container_for_input__title">
                <h1>Sign in</h1>
            </div>
            <div class="container_for_input__input">
                <input type="text" placeholder="Username" />
            </div>
            <div class="container_for_input__input">
                <input type="password" placeholder="Password" />
            </div>
            <div class="container_for_input__button">
                <button>Sign in</button>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>
