<template>
  <div class="todo-container">
    <div v-for="todo in todos" :key="todo.id">
      <TodoItem
        v-bind:item="todo"
        v-on:del-todo="$emit('del-todo', todo.id)"
        v-on:set-todo="$emit('set-todo', todo)"
      />
    </div>
  </div>
</template>
<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: "Todos",
  props: ["todos"],
  components: {
    TodoItem,
  },
};
</script>
<style scoped>
.todo-container {
  justify-content: center;
  margin: auto;
  width: 50%;
}
</style>
