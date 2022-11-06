<template>
  <li
    @mouseover="(upHere = true), (activeElId = todo.id)"
    @mouseleave="upHere = false"
    class="one-todo"
    key="todo.id"
    v-for="todo in todos"
  >
    {{ todo.title }}
    <button
      @click="deleteItem(todo.id)"
      v-show="upHere === true && activeElId === todo.id"
      class="delete-btn"
    >
      Delete
    </button>
  </li>
</template>

<script>
export default {
  data() {
    return {
      upHere: false,
      activeElId: "",
    };
  },
  emits: {
    some_func: null,
  },
  props: ["todos"],

  methods: {
    deleteItem(id) {
      this.$emit("some_func", id);
    },
  },
};
</script>

<style scoped>
.one-todo {
  height: 50px;
  border-radius: 5px;
  margin-bottom: 10px;
  width: 410px;
  list-style-type: none;
  display: flex;
  flex-direction: row;
  align-items: center;
  background: rgb(162, 160, 160);
  padding-left: 20px;
  font-size: 20px;
  font-weight: bold;
  justify-content: space-between;
}

.delete-btn {
  width: 50px;
  height: 50px;
  border: none;
  background: rgb(138, 5, 5);
  color: white;
  font-weight: bolder;
  border-radius: 0 5px 5px 0;
  text-align: center;
  display: flex;
  flex-direction: row;
  align-items: center;
  cursor: pointer;
}

.all-btn {
  display: flex;
  flex-direction: column;
  position: absolute;
  right: 30px;
  top: 198px;
  background: white;
}
</style>
