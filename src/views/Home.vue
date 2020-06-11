<template>
  <div id="app">
    <AddTodo @add-todo="addTodo" :add-loading="addLoading" />
    <Todos :todos="todos" @del-todo="deleteTodo" :delete-loading="deleteLoading"/>
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import axios from "axios";

export default {
  name: "Home",
  components: {
    AddTodo,
    Todos
  },
  data() {
    return {
      todos: [],
      addLoading: false,
      deleteLoading: []
    };
  },
  methods: {
    deleteTodo(id) {
      this.deleteLoading.push(id);
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        // eslint-disable-next-line
        .then(res => {
          this.deleteLoading = this.deleteLoading.filter(taskId => taskId !== id)
          this.todos = this.todos.filter(todo => todo.id !== id);
        })
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      this.addLoading = true;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(res => {
          console.log("res.data", res.data);
          this.addLoading = false;
          this.todos = [...this.todos, res.data];
        })
        .catch(err => console.log(err));
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err));
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
</style>
