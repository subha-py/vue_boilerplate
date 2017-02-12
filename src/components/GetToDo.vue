<template>
  <div id="get-todo">
    <div class="row">
      <div class="col-md-6">
        <input @keydown.enter="addTodos"
               class="form-control"
               :value="newTodo"
               @keypress="getTodos"
               placeholder="I need to...">
        <button class="btn btn-primary btn-sm" @click="addTodos">Add Todo</button>
      </div>
    </div>
    <CurrentToDo></CurrentToDo>
    <CompletedToDo></CompletedToDo>
  </div>
</template>

<script>
  import {mapGetters, mapActions} from 'vuex'
  import CurrentToDo from './CurrentToDo'
  import CompletedToDo from './CompletedToDo'

  export default {
    name: 'GetToDo',
    components: {
      CurrentToDo,
      CompletedToDo
    },
    methods: {
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
