<template>
  <div class="todo">
    <h1>Tarefas</h1>
    <CompletedBar :todoList="[...todos]" />
    <TodoForm @todo-added="todos = [...todos, $event]" />
    <TodoItems :todoList="[...todos]" @updatedTodo="todos = [...$event]" />
  </div>
</template>

<script>
import TodoForm from "./TodoForm.vue";
import TodoItems from "./TodoItems.vue";
import CompletedBar from "./CompletedBar.vue";

export default {
  name: "Todo",
  components: {
    TodoForm,
    TodoItems,
    CompletedBar,
  },
  data() {
    return {
      todos: [],
    };
  },
  created() {
    console.log(this.todos);
  },
};
</script>

<style>
.todo {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
}
</style>