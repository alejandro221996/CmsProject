<style>
  p{
      color: #000;
      font-size: 16px;
      font-family: Arial, Helvetica, sans-serif;
  }
  .container {
      max-width: 800px;
      width: 960px;
      margin: 0 auto;
      display: flex;
      justify-content: center;
      height: 100vh;
  }
  .navbar{
      display: flex;
      justify-content: center;
      padding: 2rem;
      background-color: #000;
    
  }
  .navbar .navbar__menu ul{
      display: flex;
      list-style: none;
      gap: 5rem;
      margin: 0;
      padding: 0;
  }
  .navbar .navbar__menu ul li a {
      text-decoration: none;
      color: #fff;
      font-size: 1.3rem;
  }
  .navbar .navbar__menu ul li a:hover {
      color: #17b0eb;
  }
  footer {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100px;
      background-color: #000;
      color: #fff;
      font-size: 1rem;
  }
  footer h2
  {
    font-weight: 100;
  }
  aside {
    width: 15%;
    padding-left: 15px;
    float: left;
    background-color: black;
    border-top-style: solid;
    border-right-style: solid;
    border-bottom-style: solid;
    border-color: #fff;
  }
  aside ul li a {
    color: #fff;
    font-size: 1.3rem;
    font-weight: 100;
    text-decoration: none;
  }
  aside ul li a:hover {
    color: #17b0eb;
  }
  aside ul li {
    margin-bottom: 1rem;
  }
</style>
<template>
  <div class="navbar">
    <div class="navbar__menu">
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </div>
  </div>
  <aside>
   <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
  </aside>
  <div>
    <slot/>
  </div>
  <footer>
      <h2>Footer</h2>
  </footer>
</template>
