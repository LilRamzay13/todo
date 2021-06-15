<template>
  <div>
    <h2>Todo List</h2>
    <router-link class="home" to="/">Home</router-link>
    <hr />
    <AddTodo @add-todo="addTodo" />
    <select class="filter" v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not Completed</option>
    </select>
    <hr />
    <Loader v-if="loading" />
    <TodoList
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />

    <p v-else>No todos!</p>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
import Loader from "@/components/Loader";

export default {
  name: "App",
  data() {
    return {
      todos: [],
      loading: true,
      filter: "all",
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=3")
      .then((response) => response.json())
      .then((json) => {
        setTimeout(() => {
          this.todos = json;
          this.loading = false;
        }, 1000);
      });
  },
  // watch:{
  // filter(value){
  //    consolole.log(value)
  //  }
  //},
  computed: {
    filteredTodos() {
      var filter;

      if (this.filter === "all") {
        filter = this.todos;
      }

      if (this.filter === "completed") {
        filter = this.todos.filter((t) => t.completed);
      }

      if (this.filter === "not-completed") {
        filter = this.todos.filter((t) => !t.completed);
      }

      return filter;
    },
  },

  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
  components: {
    TodoList,
    AddTodo,
    Loader,
  },
};
</script>

<style scoped>
.home{
  text-decoration: none;
  text-shadow:
    1px 1px 1px silver,
    -1px 1px 1px silver;
  color: rgb(91, 63, 190);
  transition: all .5s;
  font-weight: bold;
  font-size: 20px;
  font-family: 'Bradley Hand', cursive;
}

.home:hover {
  text-shadow:
    -1px -1px 1px silver,
    1px -1px 1px silver;
  color: rgb(160, 160, 160);
}

h2{
  font-family: 'Bradley Hand', cursive;
  text-shadow:
    1px 1px 1px silver,
    -1px 1px 1px silver;
}

.filter{
  margin-top: 20px;
    border: 3px solid #E6E6E6;
    border-radius: 0;
    font-weight: 400;
    color: inherit;
    padding: 11px 15px;
    line-height: normal;
    transition: border-color 0.2s ease,
                outline 0.2s ease;

 
}
</style>