<template>
  <AppHeader/>
  <AppFilter/>
  <main class="app-main">
    <AppTodoList/>
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

export default defineComponent({
  components: {AppFooter, AppAddTodo, AppTodoList, AppHeader, AppFilter}
})
</script>