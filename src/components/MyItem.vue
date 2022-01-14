<template>
  <li>
    <label>
      <input
        type="checkbox"
        :checked="todoObj.done"
        @change="checkTodo(todoObj.id)"
      />
      <!-- 如下代码也能实现功能, 只不过违反原则, 因为修改了props -->
      <!-- <input
        type="checkbox"
        v-model="todo.done"
           <input />
      /> -->
      <span>{{ todoObj.title }}</span>
    </label>
    <button class="btn btn-danger" @click="deleteToDo(todoObj.id)">删除</button>
  </li>
</template>

<script>
export default {
  name: "MyItem",
  props: ["todoObj", "handleCheck", "handleDeleteTodo"],
  methods: {
    checkTodo(id) {
      this.handleCheck(id);
      console.log(id);
    },
    deleteToDo(id) {
      if (confirm("are u sure to delete?")) {
        this.handleDeleteTodo(id);
      }
    },
  },
};
</script>

<style scoped>
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
li:hover {
  background-color: #ddd;
}
li:hover button {
  display: block;
  background-color: red;
  color: white;
}
</style>
