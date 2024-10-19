<template>
  <div id="app">
    <RouterView />
  </div>
</template>

<script setup>
import { RouterView } from 'vue-router';
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%; /* Full height */
  width: 100%; /* Full width */
}

#app {
  height: 100%; /* Full viewport height */
  width: 100%; /* Full viewport width */
  display: flex; /* Use flexbox for centering */
  align-items: center; /* Center vertically */
  justify-content: center; /* Center horizontally */
  background-color: black; /* Background color */
  color: white; /* Text color */
}
</style>
