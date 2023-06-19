<script setup>
import {ref, onMounted} from "vue";

import Header from "@/components/Header.vue";
import Tasks from "@/components/Tasks.vue";
import AddTask from "@/components/AddTask.vue";

const tasks = ref(null)
let id = 0

onMounted(() => {
  tasks.value = [
    {
      id: id++,
      text: 'Task1',
      day: 'March',
      reminder: true
    },
    {
      id: id++,
      text: 'Task2',
      day: 'June',
      reminder: true
    },
    {
      id: id++,
      text: 'Task3',
      day: 'May',
      reminder: false
    },
  ]
})

function addTask(task) {
  tasks.value.push({id: id++, ...task})
}

function deleteTask(id) {
  tasks.value = tasks.value.filter((task) => task.id !== id)
}

function toggleReminder(id) {
  tasks.value = tasks.value.map((task) =>
      task.id === id
          ? {...task, reminder: !task.reminder}
          : task
  )
}

</script>

<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <AddTask @add-task="addTask"></AddTask>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>