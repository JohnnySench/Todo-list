<template>
  <AppHeader/>
  <AppFilter @change-filter="changeFilter" :active-filter="activeFilter"/>
  <main class="app-main">
    <AppTodoList
        @remove-todo="removeTodo"
        @toggle-todo="toggleTodo"
        :todos="filteredTodos"/>
    <AppAddTodo
        @add-todo="addTodo"/>
  </main>
  <AppFooter :stats="stats"/>
</template>


<script lang="ts">

import {defineComponent} from "vue";
import AppFilter from "./components/AppFilter.vue";
import AppHeader from "./components/AppHeader.vue";
import AppTodoList from "./components/AppTodoList.vue";
import AppAddTodo from "./components/AppAddTodo.vue";
import AppFooter, {Stats} from "./components/AppFooter.vue";
import {Todo} from "./types/Todo.ts";
import {Filter} from "./types/Filter.ts";

interface State {
  todos: Todo[],
  activeFilter: Filter
}

export default defineComponent({

  components: {AppFooter, AppAddTodo, AppTodoList, AppHeader, AppFilter},
  data(): State {
    return {
      todos: [
        {id: 0, text: 'Учить TS', completed: false},
        {id: 1, text: 'Учить JS', completed: true},
        {id: 2, text: 'Учить VUE', completed: false},
      ],
      activeFilter: 'All'
    }
  },
  computed: {
    filteredTodos(): Todo[] {
      switch (this.activeFilter) {
        case 'Active': {
          return this.activeTodo
        }
        case 'Done': {
          return this.doneTodo
        }
        case 'All':
        default: {
          return this.todos
        }
      }
    },
    activeTodo() :Todo[] {
      return this.todos.filter(x => !x.completed)
    },
    doneTodo() :Todo[] {
      return this.todos.filter(x => x.completed)
    },
    stats(): Stats {
      return {
        active: this.activeTodo.length,
        done: this.doneTodo.length
      }
    }
  },
  methods: {
    changeFilter(filter: Filter) {
      this.activeFilter = filter
    },
    toggleTodo(id: number) {
      const targetTodo = this.todos.find(x => x.id === id);

      if (targetTodo) {
        targetTodo.completed = !targetTodo.completed;
      }
    },
    addTodo(data: Todo) {
      this.todos.push(data)
    },

    removeTodo(id: number) {
      this.todos = this.todos.filter(x => x.id !== id)
    }
  }
})
</script>