<template>
  <div>
    <form :class="{ loading: addLoading }">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="  Add Todo..."
        autocomplete="off"
      />
      <input
        @click="addTodo"
        type="submit"
        :value="addLoading ? 'Adding...' : 'Add' "
        class="btn btn-primary"
      />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  props: ["addLoading"],
  methods: {
    addTodo(e) {
      e.preventDefault();

      if (this.title) {
        const newTodo = {
          title: this.title,
          completed: false
        };
        this.$emit("add-todo", newTodo);
      }
    }
  }
};
</script>

<style scoped>
form {
  padding: 20px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  transform: scale(1);

  animation: fade-in-left 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);

  transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

form.loading {
  opacity: 0.5;
  pointer-events: none;
  transform: scale(0.9);
}

form input {
  margin: 0 10px;
}
</style>
