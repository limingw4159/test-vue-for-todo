<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <MyHeader :addTodo="addTodo" />
        <MyList
          :todoList="todoList"
          :handleCheck="handleCheck"
          :handleDeleteTodo="handleDeleteTodo"
        />
        <MyFooter
          :todoList="todoList"
          :handleSelectOrCancelAll="handleSelectOrCancelAll"
          :clearAllTodo="clearAllTodo"
        />
      </div>
    </div>
  </div>
</template>
<script>
import MyHeader from "./components/MyHeader.vue";
import MyFooter from "./components/MyFooter.vue";
import MyList from "./components/MyList.vue";
export default {
  name: "App",
  components: { MyHeader, MyFooter, MyList },
  data() {
    return {
      todoList: [
        { id: "001", title: "eating", done: true },
        { id: "002", title: "playing", done: false },
        { id: "003", title: "running", done: true },
      ],
    };
  },
  methods: {
    addTodo(todoObj) {
      this.todoList.unshift(todoObj);
    },
    handleCheck(id) {
      this.todoList.forEach((todo) => {
        if (todo.id === id) todo.done = !todo.done;
      });
    },
    handleDeleteTodo(id) {
      this.todoList = this.todoList.filter((todo) => todo.id !== id);
    },
    handleSelectOrCancelAll(done) {
      this.todoList.forEach((todo) => {
        todo.done = done;
      });
    },
    clearAllTodo() {
      this.todoList = this.todoList.filter((todo) => {
        return !todo.done;
      });
    },
  },
};
</script>

<style scoped>
/*base*/
body {
  background: #fff;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
