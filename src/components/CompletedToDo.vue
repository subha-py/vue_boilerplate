<template>
  <div id="completed-todo" class="row">
    <div class="col-md-6">
      <h3 v-if="completeTodos.length > 0">Completed({{completeTodos.length}})</h3>
      <ul class="list-group">
        <li class="list-group-item" v-for="todo in completeTodos">
          {{todo.body}}
          <button type="button" @click="remove(todo)" class="btn btn-default btn-sm">
            <span class="glyphicon glyphicon-remove-circle"></span> Remove
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  import {mapGetters, mapActions} from 'vuex'
  export default {
    name: 'CompletedToDo',
    methods: {
      ...mapActions(
        [
          'removeTodo'
        ]
      ),
      remove: function (todo) {
        this.removeTodo(todo)
      }
    },
    computed: {
      ...mapGetters(
        [
          'completeTodos'
        ]
      )
    }
  }
</script>
