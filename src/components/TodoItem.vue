<template>
  <div class="todo" :class="{ loading: loading }">
    <div class="card" :class="{ completed: todo.completed }">
      <input
        type="checkbox"
        @change="toggleComplete"
        :checked="todo.completed"
      />
      <p>{{ todo.title }}</p>
    </div>
    <button
      @click="$emit('del-todo', todo.id)"
      class="btn"
      :class="[loading ? 'btn-danger' : 'btn-outline-danger']"
    >
      Delete
    </button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo", "loading"],
  methods: {
    toggleComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;

  transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.todo.loading {
  opacity: 0.5;
  transform: scale(0.9);

}

.card {
  margin: 20px;
  width: min(80vw, 500px);
  padding: 10px;

  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.card input {
  position: absolute;
  left: 20px;
  top: 50%;
  transform: translateY(-50%) scale(2);
  cursor: pointer;

  transition: all 0.2s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.card input:checked {
  position: absolute;
  left: 20px;
  top: 50%;
  transform: translateY(-50%) scale(1);
  cursor: pointer;
}

.card p {
  padding: 0 50px;
  text-align: center;
}

.card.completed {
  opacity: 0.5;
}
.card.completed p {
  text-decoration: line-through;
}
</style>
