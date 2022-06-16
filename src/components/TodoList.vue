<template>
  <ul id="todoList">
    <TodoItem
      v-for="(todo, index) of todos"
      v-bind:key="index"
      v-bind:itemRemove="itemRemove"
      v-bind:itemEdit="itemEdit"
      v-bind:todo_prop="todo"
      v-bind:index="index"
    />
  </ul>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
  props: ['todos', 'itemRemove', 'itemEdit'],
  components: {
    TodoItem
  }
}
</script>

<style>
#todoList {
  margin: 0px;
  padding: 0px;
  list-style: none;
}
</style>
