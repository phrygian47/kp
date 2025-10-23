<script setup lang="ts">
import Header from "./components/Header.vue";
</script>

<template>
  <header>
    <Header></Header>
  </header>
  <NuxtPage />
</template>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

:root {
  --background-color: #eae3d7;
}

li {
  list-style: none;
}

a {
  text-decoration: none;
  color: #fff;
}

a:visited {
  color: inherit;
}

a:hover::after {
  transform: scaleX(1);
}

.container {
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  padding-left: 1rem;
  padding-right: 1rem;
}

@media (min-width: 640px) {
  .container {
    max-width: 640px;
  }
}

@media (min-width: 768px) {
  .container {
    max-width: 768px;
  }
}

@media (min-width: 1024px) {
  .container {
    max-width: 1024px;
  }
}

@media (min-width: 1280px) {
  .container {
    max-width: 1280px;
  }
}

@media (min-width: 1536px) {
  .container {
    max-width: 1536px;
  }
}
</style>
