<template>
  <div id="footer-app">
    <button v-on:click="() => {showTasks('all'); cond='all';}"
            class="button"
            v-bind:class="{'active': cond === 'all'}">
      <span>All</span>
    </button>
     <button v-on:click="() => {showTasks('active'); cond='active';}"
             class="button"
             v-bind:class="{'active': cond === 'active'}">
      <span>Active</span>
    </button>
    <button v-on:click="() => {showTasks('completed'); cond='completed';}"
            class="button"
            v-bind:class="{'active': cond === 'completed'}">
       <span>Completed</span>
    </button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      cond: 'all'
    }
  },
  props: {
    showTasks: Function
  }
}
</script>

<style scoped>
#footer-app {
  display: flex;
  justify-content: space-between;
}
.button {
  width: 30%;
}
.active {
  border: 1px solid green;
  color: white;
  background-color: green;
}
</style>
