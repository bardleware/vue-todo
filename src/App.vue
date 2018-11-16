<template>
  <div id="app">
    <h1>Due-it</h1>
    <create-todo v-on:create-todo="createTodo"/>
    <todo-item v-for="(todo, index) in todos" :key="index" v-on:toggle-todo="toggleTodo(index)" v-on:delete-todo="deleteTodo(todo.label)" v-bind:label="todo.label" v-bind:checked="todo.complete"/>
  </div>
</template>

<script>
/* eslint-disable */
import TodoItem from "./components/TodoItem.vue";
import CreateTodo from './components/CreateTodo.vue';

export default {
  name: "app",
  components: {
    TodoItem,
    CreateTodo
  },
  data: function() {
    return {
      todos: [
        {
          label: "Learn Vuejs",
          complete: false
        },
      ]
    };
  },
  methods: {
    toggleTodo: function(index) {
      this.todos[index].complete = this.todos[index].complete ? false : true; 
    },
    deleteTodo: function(label) {
      this.todos = this.todos.filter((todo) => todo.label !== label)
    },
    createTodo: function(todo) {
      this.todos.push(todo)
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 20px;
}

h1 {
  font-size: 32pt;
  color: #2c3e50;
}
</style>
