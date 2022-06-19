<template>
  <li class="list-item" v-on:click="getTodos">
    <div>
      <input type="checkbox"
             v-on:change="todo.completed = !todo_prop.completed"
             v-bind:checked="todo_prop.completed">

      <span v-bind:class="{'done': todo_prop.completed}" v-if="!todo_prop.edit">{{todo_prop.title}}</span>
      <input type="text"
             v-model="newTitle"
             v-else-if="todo_prop.edit">
    </div>
    <div>
      <button class="button edit"
              v-on:click="todo.edit = true"
              v-if="!todo_prop.edit">
        <font-awesome-icon icon="fa-solid fa-pen" class="icon"/>
      </button>
      <button class="button edit"
              v-on:click="itemEdit(newTitle, todo_prop.id)" v-else>
        <font-awesome-icon icon="fa-solid fa-square-check" class="icon"/>
      </button>
      <button class="button remove"
              v-on:click="itemRemove(todo)">
        <font-awesome-icon icon="fa-solid fa-trash" class="icon"/>
      </button>
    </div>
  </li>
</template>

<script>
export default {
  props: ['todo_prop', 'itemRemove', 'itemEdit', 'getTodos'],
  data: function () {
    return {
      todo: this.todo_prop,
      newTitle: this.todo_prop.title
    }
  }
}

</script>

<style>
.list-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  /* background-color: blue; */
  justify-content: space-between;
  padding: 5px 10px;
  border: 1px solid #749999;
  border-radius: 8px;
  margin-bottom: 5px;
}
.done {
  text-decoration:line-through
}
.button {
  border-radius: 4px;
  width: 30px;
  height: 30px;
}
.edit {
  margin-right: 10px;
  background-color: blue;
  border: 1px solid blue;
}
.remove {
  background-color: red;
  border: 1px solid red;
}
.icon {
  color: white;
}
</style>
