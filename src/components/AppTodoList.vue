<script lang="ts">
import {defineComponent, PropType} from 'vue'
import AppTodoListItem from "./AppTodoListItem.vue";
import {Todo} from "../types/Todo.ts";

export default defineComponent({
  name: "AppTodoList",
  components: {AppTodoListItem},
  emits: {
    toggleTodo: (id: number) => Number.isInteger(id),
    removeTodo: (id: number) => Number.isInteger(id)
  },
  props: {
    todos: {
      type: Array as PropType<Todo[]>
    }
  },
  methods: {
    toggleTodo(id:number) {
      this.$emit('toggleTodo', id)
    },
    removeTodo(id:number) {
      this.$emit('removeTodo', id)
    }
  }
})
</script>

<template>
  <ul class="todo-list">
    <AppTodoListItem @remove-todo="removeTodo" @toggle-todo="toggleTodo" v-for="todo in todos" :key="todo.id" :todo="todo"/>
  </ul>
</template>

<style scoped>

</style>