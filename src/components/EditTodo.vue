<template>
  <div class="input-container">
    <form class="d-flex" @submit="editTodo">
      <input placeholder="Edit Todo" v-model="title" class="w-100" required />
      <button class="btn pointer" type="submit">Update</button>
      <button class="btn-danger pointer" @click="$emit('cancel-edit', false)">
        Cancel
      </button>
    </form>
  </div>
</template>
<script>
export default {
  name: "EditTodo",
  props: {
    todo: Object,
  },
  data() {
    return {
      title: this.todo.title,
    };
  },
  methods: {
    editTodo(e) {
      e.preventDefault();
      if (this.title != "") {
        const newTodo = {
          id: this.todo.id,
          title: this.title,
        };
        this.$emit("edit-todo", newTodo, false);
        this.title = "";
      }
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
