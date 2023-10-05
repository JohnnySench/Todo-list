<script lang="ts">
import {defineComponent} from 'vue'
import AppTodoListItem from "./AppTodoListItem.vue";

export default defineComponent({
  name: "AppTodoList",
  components: {AppTodoListItem}
})
</script>

<template>
  <ul class="todo-list">
    <AppTodoListItem/>
    <li class="todo-item">
      <div class="todo-item__status">
        <i class="bi bi-check2"></i>
      </div>
      <span class="todo-item__text">Learn the basics of Typescript</span>
      <button class="todo-item__remove-button">
        <i class="bi bi-trash3"></i>
      </button>
    </li>
    <li class="todo-item">
      <div class="todo-item__status">
        <i class="bi bi-check2"></i>
      </div>
      <span class="todo-item__text">Subscribe to the channel</span>
      <button class="todo-item__remove-button">
        <i class="bi bi-trash3"></i>
      </button>
    </li>
  </ul>
</template>

<style scoped>

</style>