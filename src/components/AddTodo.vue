<template>
  <div id="addTodo">
    <input type="text"
           v-model="title"
           placeholder="Add Task Title"
           class="textInput"
    >
    <button v-on:click="() => {itemAdd(title); title='';}" class="button edit">
      <font-awesome-icon icon="fa-solid fa-plus" class="icon"/>
    </button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: ''
    }
  },
  props: {
    itemAdd: Function
  }
}
</script>

<style scoped>
#addTodo {
    margin: 10px 0;
    display: flex;
    flex-direction: row;
    align-items: center;
    /* flex-wrap: wrap; */
}
.edit{
  margin-right: 0;
  margin-left: 10px;
  background-color: green;
  border-color: green;
  width: 40px;
  height: 40px;
}
.textInput {
  border: 1px solid;
  border-radius: 4px;
  padding: 10px;
  /* width: 100%; */
  flex: 1;
}
</style>
