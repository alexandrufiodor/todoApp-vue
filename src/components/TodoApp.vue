<template>
  <div>
    <AddTodo v-bind:itemAdd="itemAdd"/>
    <hr />

    <div v-if="todos.length > 0">
      <TodoList v-bind:todos_temp="copyTodos.length > 0 ? copyTodos : todos"
                v-bind:itemRemove="itemRemove"
                v-bind:itemEdit="itemEdit"
      />
      <hr />
      <FooterApp v-bind:showTasks="showTask"/>
    </div>
    <p v-else>No Tasks</p>
  </div>
</template>

<script>
import TodoList from './TodoList.vue'
import AddTodo from './AddTodo.vue'
import FooterApp from './FooterApp.vue'

export default {
  components: {
    TodoList,
    AddTodo,
    FooterApp
  },
  data () {
    return {
      todos: [],
      copyTodos: []
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
        localStorage.setItem('todos', JSON.stringify(this.todos))
      },
      deep: true
    }
  },
  methods: {
    itemAdd (title) {
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
    },
    showTask (cond) {
      if (cond === 'active') {
        this.copyTodos = this.todos.filter(todo => todo.completed === false)
        console.log('this.copyTodos active', this.copyTodos)
        console.log('JSON.parse(localStorage.getItem active', JSON.parse(localStorage.getItem('todos')))
      } else if (cond === 'completed') {
        this.copyTodos = this.todos.filter(todo => todo.completed === true)
        console.log('this.copyTodos completed', this.copyTodos)
        console.log('JSON.parse(localStorage.getItem completed', JSON.parse(localStorage.getItem('todos')))
      } else if (cond === 'all') {
        this.copyTodos = this.todos
        console.log('this.copyTodos all', this.copyTodos)
        console.log('JSON.parse(localStorage.getItem all', JSON.parse(localStorage.getItem('todos')))
      }
    }
  }
}
</script>
