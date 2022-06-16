<template>
  <div>
    <AddTodo v-bind:itemAdd="itemAdd"/>
    <hr />

    <div v-if="todos.length > 0">
      <TodoList v-bind:todos="todos"
                v-bind:itemRemove="itemRemove"
                v-bind:itemEdit="itemEdit"
      />
    </div>
    <p v-else>No Tasks</p>
  </div>
</template>

<script>
import TodoList from './TodoList.vue'
import AddTodo from './AddTodo.vue'

export default {
  components: {
    TodoList,
    AddTodo
  },
  data () {
    return {
      todos: []
    }
  },
  mounted () {
    if (localStorage.getItem('todos')) {
      this.todos = JSON.parse(localStorage.getItem('todos'))
    }
  },
  watch: {
    todos: {
      handler () {
        console.log('test')
        localStorage.setItem('todos', JSON.stringify(this.todos))
      },
      deep: true
    }
  },
  methods: {
    itemAdd (title) {
      console.log('todos', this.todos.map(item => console.log(item.title)))
      if (title.trim()) {
        this.todos.push({ id: new Date(), title: title, completed: false, edit: false })
      } else {
        alert('Add title task')
      }
    },
    itemEdit (title, id) {
      const objIndex = this.todos.findIndex(obj => obj.id === id)
      this.todos[objIndex].title = title
      this.todos[objIndex].edit = false
    },
    itemRemove (item) {
      this.todos = this.todos?.filter(todo => todo.id !== item.id)
    }
  }
}
</script>
