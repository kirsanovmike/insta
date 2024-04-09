<template>
<div style="display: flex; align-items: center">
  <img v-for="post in posts" :key="post.id" :src="post.image" style="margin-left: 12px; width: 200px; height: 200px" />
</div>
</template>

<script setup lang="ts">
interface Image {
  id: number,
  image?: string
}

interface Props {
  posts: Image[]
}

withDefaults(defineProps<Props>(), {
  posts: () => []
})
</script>
