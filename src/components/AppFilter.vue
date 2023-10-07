<script lang="ts">
import {defineComponent, PropType} from 'vue'
import {Filter} from "../types/Filter.ts";
interface State {
  filters: Filter[]
}

export default defineComponent({
  name: "AppFilter",
  emits: {
    changeFilter: (filter: Filter) => filter
  },
  props: {
    activeFilter: {
      type: String as PropType<Filter>,
      required: true
    }
  },
  data(): State {
    return {
      filters: ['All', 'Active', 'Done']
    }
  },
  methods: {
    changeFilter(filter: Filter) {
      this.$emit('changeFilter', filter)
    }
  }
})
</script>

<template>
  <aside class="app-filters">
    <section class="toggle-group">
      <button
          @click="changeFilter(filter)"
          v-for="filter in filters"
          :key="filter"
          class="button"
          :class="{'button--primary': activeFilter === filter}">{{filter}}</button>
    </section>
  </aside>
</template>

<style scoped>

</style>