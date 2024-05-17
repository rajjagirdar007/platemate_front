<template>
  <div id="app">
    <h3 class="platemate title has-text-centered">PlateMate</h3>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/post">Post</router-link> |
      <router-link to="/feed2">feed2</router-link> |
      <router-link to="/feed">Feed</router-link>
    </nav>
    <router-view/>
  </div>
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
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: rgba(206, 68, 41, 1);
}

/* Add this rule to style the PlateMate h1 element */
.title.platemate {
  color: rgba(206, 68, 41, 1);
  font: cursive;
}
</style>
