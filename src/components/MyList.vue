<template>
  <ul class="todo-main">
    <MyItem
      v-for="todoObj in todoList"
      :key="todoObj.id"
      :todoObj="todoObj"
      :handleCheck="handleCheck"
      :handleDeleteTodo="handleDeleteTodo"
    />
  </ul>
</template>
<script>
import MyItem from "./MyItem.vue";

export default {
  name: "MyList",
  components: { MyItem },
  props: ["todoList", "handleCheck", "handleDeleteTodo"],
};
</script>

<style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
