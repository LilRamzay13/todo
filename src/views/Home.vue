<template>
  <div>
    <h2>Home page</h2>

    <p>
      Lorem, ipsum dolor sit amet consectetur adipisicing elit. Doloribus
      magnam, magni reiciendis voluptatem sequi laborum porro officiis minima.
      Nam, recusandae vero? Neque inventore, reprehenderit id velit facilis
      facere odit porro!
    </p>

    <router-link class="todos" to="/todos">Todos</router-link>
  </div>
</template>

<style scoped>
.todos {
  text-decoration: none;
  outline: none;

  text-shadow: 1px 1px 1px silver, -1px 1px 1px silver;
  color: rgb(91, 63, 190);
  transition: all 0.5s;
  font-weight: bold;
  font-size: 20px;
  font-family: "Bradley Hand", cursive;
}

.todos:hover {
  color: rgb(194, 165, 165);
  transition: 0.9s;
  text-shadow: -1px -1px 1px silver, 1px -1px 1px silver;
  color: rgb(160, 160, 160);
}

h2 {
  font-family: "Bradley Hand", cursive;
  text-shadow: 1px 1px 1px silver, -1px 1px 1px silver;
}

p {
  font-family: "Bradley Hand", cursive;
  width: 50%;
  margin: 0 auto;
  margin-bottom: 20px;
}
</style>