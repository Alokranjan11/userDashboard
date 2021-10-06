<template>
  <div id="nav">
  </div>
  <router-view />
</template>

<style>
#app {
   font-family: 'Abhaya Libre';font-size: 22px;;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #EFF6FF;
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
