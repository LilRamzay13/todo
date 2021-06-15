<template>
  <div id="app">
    <h1>Todo Aplication</h1>
    <hr>

    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Snell Roundhand, cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  text-shadow:
    1px 1px 1px rgb(61, 55, 55),
    -1px 1px 1px silver;
}
</style>
