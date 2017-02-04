<template>
  <div id="get-todo" class="container">
    <input class="form-control"
           :value="newTodo"
           @change="getTodo"
           placeholder="I need to...">
    <button class="btn btn-primary" @click="addTodo">Add Todo</button>
  </div>
</template>
<script>
  export default {
    methods: {
      getTodo: function (e) {
        this.$store.dispatch('getTodo', e.target.value)
      },
      addTodo: function () {
        this.$store.dispatch('addTodo')
        this.$store.dispatch('clearTodo')
      }
    },
    computed: {
      newTodo: function () {
        return this.$store.getters.newTodo
      }
    }
  }
</script>
