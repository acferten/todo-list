<script setup>
defineProps(['text', 'color'])

function onClick() {
  console.log("click")
}
</script>

<template>
  <button :style="{background: color}" class="btn" @click="onClick">{{ text }}</button>
</template>

<style scoped>
</style>