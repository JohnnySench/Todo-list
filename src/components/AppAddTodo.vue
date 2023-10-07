<script lang="ts">
import {defineComponent} from 'vue'
import {Todo} from "../types/Todo.ts";

interface State {
  isFormVisible: boolean,
  nameTodo: string
}

export default defineComponent({
  name: "AppAddTodo",
  emits: {
    addTodo: (todo: Todo) => todo
  },
  data(): State {
    return {
      isFormVisible: false,
      nameTodo: ''
    }
  },
  methods: {
    showForm() {
      this.isFormVisible = true
    },
    closeForm() {
      this.isFormVisible = false
    },
    addTodo() {
      this.$emit('addTodo', {
        id: Date.now(),
        text: this.nameTodo,
        completed: false
      })
      this.nameTodo = ''
    }
  }

})
</script>

<template>
  <section class="add-todo">
    <form @submit.prevent="addTodo" v-if="isFormVisible" class="add-todo__form">
      <button @click="closeForm" class="close-button" type="button">
        <i class="bi bi-x"></i>
      </button>
      <div class="text-input text-input--focus">
        <input v-model="nameTodo" class="input"/>
      </div>
      <button class="button button--filled">Add task</button>
    </form>
    <button @click="showForm" v-else class="add-todo__show-form-button">
      <i class="bi bi-plus-lg"></i>
    </button>
  </section>
</template>

<style scoped>

</style>