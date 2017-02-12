<template>
  <div id="current-todo" class="row">
    <div class="col-md-6">
      <h3 v-if="todos.length > 0">Current({{todos.length}})</h3>
      <ul class="list-group">
        <li class="list-group-item" v-for="todo in todos">
          {{todo.body}}
          <div class="btn-group">
            <button type="button" @click="edit(todo)" class="btn btn-primary">
              <span class="glyphicon glyphicon-edit"></span> Edit
            </button>
            <button type="button" @click="complete(todo)" class="btn btn-success">
              <span class="glyphicon glyphicon-ok-circle"></span> Complete
            </button>
            <button type="button" @click="remove(todo)" class="btn btn-danger">
              <span class="glyphicon glyphicon-remove-circle"></span> Remove
            </button>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>


<script>
  import {mapGetters, mapActions} from 'vuex'
  export default{
    name: 'CurrentToDo',
    methods: {
      ...mapActions(
        [
          'editTodo',
          'completeTodo',
          'removeTodo'
        ]
      ),
      edit: function (todo) {
        this.editTodo(todo)
      },
      complete: function (todo) {
        this.completeTodo(todo)
      },
      remove: function (todo) {
        this.removeTodo(todo)
      }
    },
    computed: {
      ...mapGetters(
        [
          'todos'
        ]
      )
    }
  }
</script>
<style>
  .btn-group{
    float: right;
  }
</style>
