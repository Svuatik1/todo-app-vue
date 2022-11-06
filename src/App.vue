<template>
  <TodoList :todos="todos" @btn-add-todo="addTodo" @delete-item="deleteItem" />
</template>

<script>
import TodoList from "@/components/TodoList.vue";
export default {
  data() {
    return {
      todos: [
        { id: 1, title: "Buy product", done: false },
        { id: 2, title: "Call to best friend", done: false },
        { id: 3, title: "Go walk with dog", done: false },
        { id: 4, title: "Clean kitchen", done: false },
      ],
      newItem: {},
    };
  },
  components: {
    TodoList,
  },
  methods: {
    addTodo(value) {
      this.newItem = {
        id: Math.floor(Math.random() * 99999),
        title: value,
        done: false,
      };
      this.todos.push(this.newItem);
    },
    deleteItem(id) {
      if (id === undefined) {
        this.todos = [];
      } else this.todos = this.todos.filter((item) => item.id !== id);
    },
  },
};
</script>

<style>
* {
  background: linear-gradient(to right, rgb(76, 216, 216), rgb(22, 229, 119));
}
</style>
