<template>
  <div>
    <!--<div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/postit">Post-it</router-link> |
      <router-link to="/test">Test</router-link> |
      <router-link to="/about">About</router-link>
    </div>-->
    <router-view />
  </div>
</template>

<script>

export default {
  name: "Home",
  components: {
    //
  }
};
</script>

<style>
body {
  background-image: url(assets/Lightblue_empty_grid.svg);
  background-size: cover;
  background-repeat: repeat;
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
