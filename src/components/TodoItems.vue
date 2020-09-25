<template>
  <div class="todo-items">
    <div
      v-for="item in todoList"
      :key="item.id"
      :class="{ completed: item.completed }"
      class="item"
      @click="completeTodo(item.id)"
    >
      <span :class="{ line: item.completed }">{{ item.todo }}</span>
      <button
        class="delete"
        @click="deleteTask(item.id)"
        :style="{
          backgroundColor: item.completed
            ? ' rgb(6, 185, 6)'
            : ' rgb(245, 78, 111)',
        }"
      >
        x
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItems",
  props: {
    todoList: Array,
  },
  methods: {
    completeTodo(id) {
      const updatedTodo = this.todoList.map((item) => {
        if (item.id === id) {
          item.completed = !item.completed;
        }
        return item;
      });
      this.$emit("updatedTodo", updatedTodo);
    },
    deleteTask(id) {
      const updatedTodo = this.todoList.filter((item) => item.id !== id);
      this.$emit("updatedTodo", updatedTodo);
    },
  },
};
</script>

<style scoped>
.todo-items {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.item {
  position: relative;
  width: 200px;
  height: 100px;
  background-color: crimson;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px;
  border-radius: 6px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
}
.completed {
  background-color: green;
  color: white;
}

.delete {
  outline: none;
  border-radius: 10px;
  color: white;
  border: none;
  position: absolute;
  top: 10px;
  right: 10px;
}

.line {
  text-decoration: line-through;
}
</style>