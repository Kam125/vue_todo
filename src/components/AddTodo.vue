<template>
  <div class="input-container">
    <form class="d-flex" @submit="addTodo">
      <input placeholder="AddTodo" v-model="title" class="w-100" required />
      <button class="btn pointer" type="submit">Add</button>
    </form>
  </div>
</template>
<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: Date.now(),
        title: this.title,
      };
      this.$emit("add-todo", newTodo);
      this.title = "";
    },
  },
};
</script>
<style scoped>
.input-container {
  width: 50%;
  margin: auto;
}
</style>
