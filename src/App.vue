<template>
  <AppHeader/>
  <AppFilter/>
  <main class="app-main">
    <AppTodoList @toggle-todo="toggleTodo" :todos="todos"/>
    <AppAddTodo/>
  </main>
  <AppFooter/>
</template>


<script lang="ts">

import {defineComponent} from "vue";
import AppFilter from "./components/AppFilter.vue";
import AppHeader from "./components/AppHeader.vue";
import AppTodoList from "./components/AppTodoList.vue";
import AppAddTodo from "./components/AppAddTodo.vue";
import AppFooter from "./components/AppFooter.vue";
import {Todo} from "./types/Todo.ts";

interface State {
  todos: Todo[]
}

export default defineComponent({

  components: {AppFooter, AppAddTodo, AppTodoList, AppHeader, AppFilter},
  data(): State {
    return {
      todos: [
        {id: 0, text: 'Учить TS', completed: false},
        {id: 1, text: 'Учить JS', completed: true},
        {id: 2, text: 'Учить VUE', completed: false},
      ]
    }
  },
  methods: {
    toggleTodo(id: number) {
      const targetTodo = this.todos.find(x => x.id === id);

      if (targetTodo) {
        targetTodo.completed = !targetTodo.completed;
      }
    }
  }
})
</script>