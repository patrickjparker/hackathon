<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Plan</router-link> |
      <router-link to="/profile">Profile</router-link> |
      <router-link to="/shoppingcart">Shopping Cart</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
:root {
  --color-success: #8bde8b;
  --color-meal: #d2d2d2;
  --color-meal-border: #fff70b;
  --color-day: #78aeff;
  
  --color-primary: #ff0000;
  --color-dark: #000000;
  --color-light: #ffffff;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
