<template>
  <div id="app"  class="container">
    <ul class="nav nav-tabs">
      <!--set 'active' class conditionally-->
      <li v-for="page in pages" :class="isActivePage(page) ? 'active' : '' ">
        <!--use links to change between tabs-->
        <a @click="setPage(page)">{{page}}</a>
      </li>
    </ul>
    <component :is="activePage"></component>
  </div>
</template>

<script>
  import Vue from 'vue'
  import VueMaterial from 'vue-material'
  import GetToDo from './components/GetToDo'
  import CurrentToDo from './components/CurrentToDo'
  import CompletedToDo from './components/CompletedToDo'

  Vue.use(VueMaterial)

  export default {
    name: 'app',
    components: {
      GetToDo,
      CurrentToDo,
      CompletedToDo
    },
    data () {
      return {
        pages: [
          'GetToDo',
          'CurrentToDo',
          'CompletedToDo'
        ],
        activePage: 'GetToDo'
      }
    },
    methods: {
      setPage (newPage) {
        this.activePage = newPage
      },
      isActivePage (page) {
        return this.activePage === page
      }
    }
  }
</script>
