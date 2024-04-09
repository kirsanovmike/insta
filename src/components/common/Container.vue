<script setup lang="ts">
interface Props {
  flex: boolean
}

withDefaults(defineProps<Props>(), {
  flex: false
})
</script>

<template>
  <div class="container" :style="flex  ? 'display: flex; align-items: center; justify-content: space-between;' : undefined">
    <slot />
  </div>
</template>

<style scoped>
.container {
  width: 1000px;
  margin: 0 auto;
}
</style>