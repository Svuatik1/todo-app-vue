<template>
  <div class="main-box">
    <h1 class="title">Todo App</h1>
    <form class="add-form" action="add">
      <input
        v-model="inputValue"
        class="add-input"
        type="text"
        placeholder="input what todo..."
      />
      <button class="add-btn" @click.prevent="btnAddTodo">+</button>
    </form>
    <ul>
      <SimpleTodoVue :todos="todos" @some_func="someFucn" />
    </ul>
    <div class="footer">
      <h2 style="background: white">Total count of task: {{ todos.length }}</h2>
      <button class="clear-btn" @click="clearTasks">Clear all</button>
    </div>
  </div>
</template>

<script>
import SimpleTodoVue from "./SimpleTodo.vue";
export default {
  data() {
    return {
      inputValue: "",
    };
  },
  components: {
    SimpleTodoVue,
  },
  props: ["todos"],
  methods: {
    btnAddTodo() {
      if (this.inputValue) {
        this.$emit("btn-add-todo", this.inputValue);
        this.inputValue = "";
      }
    },
    someFucn(id) {
      this.$emit("delete-item", id);
    },
    clearTasks() {
      this.someFucn();
    },
  },
};
</script>

<style scoped>
.main-box {
  position: relative;
  background: white;
  width: 500px;
  min-height: 265px;
  border-radius: 20px;
  margin: 150px auto;
  padding-bottom: 10px;
}
.title {
  position: relative;
  background: white;
  padding-left: 30px;
  padding-top: 30px;
  border-radius: 20px;
}
.add-form {
  position: relative;
  background: white;
}
.add-input {
  background: white;
  width: 350px;
  height: 45px;
  border-radius: 5px;
  margin: 20px 20px 20px 35px;
  text-indent: 10px;
}
.add-btn {
  font-size: 20px;
  color: white;
  font-weight: bolder;
  background: rgb(142, 27, 152);
  height: 50px;
  width: 50px;
  border-radius: 5px;
  margin: 20px 20px 20px 5px;
}
ul {
  background: white;
  margin-left: 0;
  margin-bottom: 0;
}
.footer {
  display: flex;
  margin: 0 30px 0 45px;
  justify-content: space-between;
  background: white;
}
.clear-btn {
  height: 50px;
  width: 50px;
  background: rgb(142, 27, 152);
  border-radius: 5px;
  width: 70px;
  color: white;
  font-weight: bolder;
  cursor: pointer;
}
</style>
