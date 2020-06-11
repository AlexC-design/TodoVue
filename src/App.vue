<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>

<script>
import Header from "./components/layout/Header";

export default {
  name: "app",
  components: {
    Header
  }
};
</script>

<style>
html {
  font-family: Arial, Helvetica, sans-serif;
}

body * {
  margin: 0;
  padding: 0;
}

#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

@keyframes fade-in-top {
  0% {
    opacity: 0;
    transform: translateY(-200px);
  }
  20% {
    opacity: 0;
  }
  800% {
    transform: translateY(0);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fade-in-left {
  0% {
    opacity: 0;
    transform: translateX(-200px);
  }
  20% {
    opacity: 0;
  }
  800% {
    transform: translateX(0);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fade-in-right {
  0% {
    opacity: 0;
    transform: translateX(200px);
  }
  20% {
    opacity: 0;
  }
  800% {
    transform: translateX(0);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>
