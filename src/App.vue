<template>
<nav>
  <div id="logo">
    <img src="./assets/images/1294077.svg" class="app-logo" alt="Logotipo" />
  </div>

    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
  height: 120px;
  width: 100%;
  background: white;
  border-bottom: 1px solid #ccc;
  border-top: 3px solid #09a330;

}

nav a {
  font-size: 25px;
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  transition: 300ms all;
  
}

a:hover {
    color: #3cb2d3;
    
}

nav a.router-link-exact-active {
  color: #42b983;
}

#logo img {
    height: 50px;
    float: left;
    margin-top: 30px;
    margin-left: 200px;
    animation: girar infinite 30s linear;

}

@keyframes girar {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

</style>
