<script lang="ts">
import {defineComponent, PropType} from 'vue'

export interface Stats {
  active: number,
  done: number
}
export default defineComponent({
  name: "AppFooter",
  props: {
    stats: {
      type: Object as PropType<Stats>,
      required: true
    }
  }
})
</script>

<template>
  <footer class="app-footer">{{stats.active}} more to do, {{stats.done}} done</footer>

</template>

<style scoped>

</style>