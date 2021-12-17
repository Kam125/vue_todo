<template>
  <div id="app">
    <Header />
    <div v-if="!isEditing">
      <AddTodo v-on:add-todo="addTodo" />
    </div>
    <div v-else>
      <EditTodo
        v-on:edit-todo="editTodo"
        v-bind:todo="todo"
        v-on:cancel-edit="cancelEdit"
      />
    </div>
    <Todos
      v-bind:todos="todos"
      v-on:del-todo="deleteTodo"
      v-on:set-todo="setTodo"
    />
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import Header from "./components/Header.vue";
import AddTodo from "./components/AddTodo.vue";
import EditTodo from "./components/EditTodo.vue";
export default {
  name: "App",
  components: {
    Header,
    Todos,
    AddTodo,
    EditTodo,
  },
  data() {
    return {
      todos: [],
      isEditing: false,
      todo: {},
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
      alert("Todo Deleted Successfully");
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
      alert("Todo Added Successfully");
    },
    editTodo(newTodo, val) {
      this.todos = [
        ...this.todos.filter((todo) => todo.id != newTodo.id),
        { title: newTodo.title, id: newTodo.id },
      ];
      this.isEditing = val;
      alert("Todo Updated Successfully");
    },
    setTodo(item) {
      this.todo = item;
      this.isEditing = true;
    },
    cancelEdit(val) {
      this.isEditing = val;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.pointer {
  cursor: pointer;
}
.btn {
  display: inline-block;
  background: #555;
  color: #fff;
  padding: 10px 30px;
}
.btn:hover {
  background: #666;
}
</style>
