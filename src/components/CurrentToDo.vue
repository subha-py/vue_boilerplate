<template>
  <div id="current-todos" class="container">
    <h3 v-if="todos.length > 0">Current({{todos.length}})</h3>
    <ul class="list-group">
      <li class="list-group-item" v-for="todo in todos">
        {{todo.body}}
        <div class="btn-group">
          <button type="button" @click="edit(todo)" class="btn btn-default btn-sm">
            <span class="glyphicon glyphicon-edit"></span> Edit
          </button>
          <button type="button" @click="complete(todo)" class="btn btn-default btn-sm">
            <span class="glyphicon glyphicon-ok-circle"></span> Complete
          </button>
          <button type="button" @click="remove(todo)" class="btn btn-default btn-sm">
            <span class="glyphicon glyphicon-remove-circle"></span> Remove
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
  export default{
    methods: {
      edit: function (todo) {
        this.$store.dispatch('editTodo', todo)
      },
      complete: function (todo) {
        this.$store.dispatch('completeTodo', todo)
      },
      remove: function (todo) {
        this.$store.dispatch('removeTodo', todo)
      }
    },
    computed: {
      todos: function () {
        return this.$store.getters.todos
      }
    }
  }
</script>
<style>
  .btn-group{
    float: right;
  }
</style>
