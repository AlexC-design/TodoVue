<template>
  <header class="header">
    <h2>Todo List</h2>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style>
.header {
  background: rgb(36, 37, 37);
  width: 100%;
  padding: 40px;
  text-align: center;
  color: white;
}

#nav {
  color: lightblue;
}

#nav a {
  color: lightblue;
}
#nav a:hover {
  color: rgb(96, 179, 206);
}
#nav a:active {
  color: white;
}
</style>
