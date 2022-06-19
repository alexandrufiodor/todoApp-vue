<template>
  <ul id="todoList">
    <TodoItem
      v-for="(todo, index) of todos_temp"
      v-bind:key="index"
      v-bind:itemRemove="itemRemove"
      v-bind:itemEdit="itemEdit"
      v-bind:todo_prop="todo"
      v-bind:index="index"
      v-bind:getTodos="getTodos"
    />
  </ul>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
  props: ['todos_temp', 'itemRemove', 'itemEdit'],
  methods: {
    getTodos () {
      console.log('todos_temp', this.todos_temp)
    }
  },
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
