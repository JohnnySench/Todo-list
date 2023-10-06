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
  }
})
</script>

<template>
  <ul class="todo-list">
    <AppTodoListItem v-for="todo in todos" :key="todo.id" :todo="todo"/>
  </ul>
</template>

<style scoped>

</style>