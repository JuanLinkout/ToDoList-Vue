<template>
  <div>
    <input class="input" @keyup.enter="addTodo" v-model="newTodo" type="text" />
    <button class="button" @click="addTodo">Add</button>
  </div>
</template>

<script>
export default {
  name: "TodoForm",
  data() {
    return {
      newTodo: "",
      currentId: 0,
    };
  },
  methods: {
    addTodo() {
      if (!this.newTodo) {
        return;
      }

      const id = this.currentId + 1;
      const todo = this.newTodo;
      const completed = false;

      this.$emit("todo-added", { todo, id, completed });

      this.newTodo = "";
      this.currentId = id;
    },
  },
};
</script>

<style scoped>
.input {
  outline: none;
  border: none;
  border-bottom: solid 2px grey;
}

.input:focus {
  border-bottom: solid 2px royalblue;
}

.button {
  border: solid 2px grey;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  outline: none;
  border-radius: 6px;
  margin: 5px;
  background-color: grey;
  color: white;
}
.button:hover {
  border: solid 2px darkgrey;
  background-color: darkgrey;
}

.button:active {
  border: solid 2px royalblue;
  background-color: royalblue;
}
</style>