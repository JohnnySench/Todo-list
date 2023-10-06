<script lang="ts">
import {defineComponent, PropType} from 'vue'
import {Todo} from "../types/Todo.ts";

export default defineComponent({
  name: "AppTodoListItem",
  emits: {
    toggleTodo: (id: number) => Number.isInteger(id)
  },
  props: {
    todo: {
      type: Object as PropType<Todo>,
      required: true
    }
  },
  methods: {
    toggleTodo() {
      this.$emit('toggleTodo', this.todo.id)
    }
  }
})
</script>

<template>
  <li class="todo-item" :class="{'todo-item--done' : todo.completed}" @click="toggleTodo">
    <div class="todo-item__status">
      <i class="bi bi-check2"></i>
    </div>
    <span class="todo-item__text">{{todo.text}}</span>
    <button class="todo-item__remove-button">
      <i class="bi bi-trash3"></i>
    </button>
  </li>
</template>

<style scoped>

</style>