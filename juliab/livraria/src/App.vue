<script setup>
import HeaderComp from "../src/components/HeaderComp.vue";
</script>

<template>
  <HeaderComp />
  <main>
    <RouterView />
  </main>
</template>

<style>
@import "@/assets/base.css";
@import "@/assets/style.css";


#app {
  max-width: 1580px;
  margin: 0 auto;
  font-weight: normal;
  height: 100vh;
}
header {
  background-color: rgba(140, 81, 170, 0.816);
  color: rgb(255, 255, 255);
  height: 15%;
  font-size: 1.8em;
  display: flex;
  align-items: center;
  padding-left: 2rem;
}
main {
  height: 70%;
}
a {
  color: inherit;
  text-decoration: none;
  height: 10%;
}
</style>
