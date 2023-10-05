<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: "AppTodoListItem"
})
</script>

<template>
  <li class="todo-item todo-item--done">
    <div class="todo-item__status">
      <i class="bi bi-check2"></i>
    </div>
    <span class="todo-item__text">Learn the basics of Vue</span>
    <button class="todo-item__remove-button">
      <i class="bi bi-trash3"></i>
    </button>
  </li>
</template>

<style scoped>

</style>