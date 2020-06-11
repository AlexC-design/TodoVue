<template>
  <div class="items-container">
    <div :key="todo.id" v-for="todo in todos">
      <TodoItem
        :todo="todo"
        :loading="deleteLoading.includes(todo.id)"
        @del-todo="$emit('del-todo', todo.id)"
      />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos", "deleteLoading"]
};
</script>

<style>
.items-container {
  max-width: 1200px;
  margin: 20px auto;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  animation: fade-in-right 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
</style>
