<template>
  <div class="todo-item">
    <div class="d-flex">
      <h6>{{ item.title }}</h6>
      <div class="ms-auto">
        <i
          class="fa fa-pencil-alt text-info pointer"
          @click="$emit('set-todo', item)"
        ></i>
        <i
          class="fa fa-trash ms-3 text-danger pointer"
          @click="$emit('del-todo', item.id)"
        ></i>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "TodoItem",
  props: { item: Object },
};
</script>
<style scoped>
.todo-item {
  text-align: left;
  background-color: aliceblue;
  padding: 10px;
  border: 1px #000000 dotted;
}
</style>
