<template>
  <div id="get-todo" class="row">
    <div class="col-md-6">
    <input @keydown.enter="addTodos"
           class="form-control"
           :value="newTodo"
           @keypress="getTodos"
           placeholder="I need to...">
    <button class="btn btn-primary btn-sm" @click="addTodos">Add Todo</button>
      </div>
  </div>
</template>

<script>
  import {mapGetters, mapActions} from 'vuex'

  export default {
    methods: {
      name: 'GetToDo',
      ...mapActions(
        [
          'getTodo',
          'addTodo',
          'clearTodo'
        ]
      ),
      getTodos: function (e) {
        this.getTodo(e.target.value)
      },
      addTodos: function () {
        this.addTodo()
        this.clearTodo()
      }
    },
    computed: {
      ...mapGetters(
        [
          'newTodo'
        ]
      )
    }
  }
</script>
