<script lang="ts">
import {defineComponent, PropType} from 'vue'
import AppTodoListItem from "./AppTodoListItem.vue";

export default defineComponent({
  name: "AppTodoList",
  components: {AppTodoListItem},
  props: {
    todos: {
      type: Array as PropType<any>
    }
  },
  methods: {
    toggleTodo(id:number) {
      this.$emit('toggleTodo', id)
    }
  }
})
</script>

<template>
  <ul class="todo-list">
    <AppTodoListItem @toggle-todo="toggleTodo(todo.id)" v-for="todo in todos" :key="todo.id" :todo="todo"/>
  </ul>
</template>

<style scoped>

</style>