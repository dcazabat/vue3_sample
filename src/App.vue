<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Todo from './components/Todo.vue'

</script>

<template>
  <header>
    <div class="m-3">
      <label for="" class="display-6">App Vue.js 3 de Ejemplo</label>
    </div>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <Todo />
      <!-- <HelloWorld msg="Hola Mundo" /> -->
    </div>
  </header>

  <main>
    <!-- <TheWelcome /> -->
  </main>
</template>

<style>
/* @import './assets/base.css'; */

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
