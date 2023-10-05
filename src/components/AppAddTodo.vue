<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: "AppAddTodo"
})
</script>

<template>
  <section class="add-todo">
    <button class="add-todo__show-form-button">
      <i class="bi bi-plus-lg"></i>
    </button>
    <form class="add-todo__form">
      <button class="close-button" type="button">
        <i class="bi bi-x"></i>
      </button>
      <div class="text-input text-input--focus">
        <input class="input"/>
      </div>
      <button class="button button--filled">Add task</button>
    </form>
  </section>
</template>

<style scoped>

</style>