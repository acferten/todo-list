<script setup>
import Task from "@/components/Task.vue";

defineProps(['tasks'])
defineEmits(['delete-task', 'toggle-reminder'])

</script>

<template>
  <div v-for="task in tasks" :key="tasks.id">
    <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)"
          :task="task"/>
  </div>
</template>

<style scoped>

</style>