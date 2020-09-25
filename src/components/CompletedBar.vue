<template>
  <div class="borda-barra">
    <div class="barra" :style="{ width: numberCompletedTodos + '%' }"></div>
    <span>{{ numberCompletedTodos + "%" }}</span>
  </div>
</template>

<script>
export default {
  name: "TodoItems",
  props: {
    todoList: Array,
  },
  computed: {
    numberCompletedTodos() {
      const completedTodo = this.todoList.filter((item) => item.completed);
      const total = this.todoList.length;
      const completed = completedTodo.length;
      const result = Math.floor((completed * 100) / total);
      return result || 0;
    },
  },
};
</script>

<style scoped>
.borda-barra {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-items: center;
  width: 500px;
  border-radius: 10px;
  background-color: lightgrey;
  text-align: center;
  color: white;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  margin: 30px;
}

.borda-barra span {
  z-index: 1;
  font-size: 1.5em;
}

.barra {
  position: absolute;
  border-radius: 10px;
  height: 100%;
  color: white;
  background-color: green;
}
</style>