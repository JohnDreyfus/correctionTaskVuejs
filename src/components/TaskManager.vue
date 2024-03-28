<script setup>
import { defineProps, ref, computed, onMounted, watch } from 'vue'
import TaskItem from './TaskItem.vue'
import Compteur from './Compteur.vue'
import FilterTasks from './FilterTasks.vue'
import FormTask from './FormTask.vue'

const tasks = ref([])

onMounted(() => {
  const savedTasks = localStorage.getItem('tasks')
  tasks.value = savedTasks ? JSON.parse(savedTasks) : []
})

const addTask = (newTaskText) => {
  tasks.value.push({
    id: tasks.value.length + 1,
    task: newTaskText,
    isComplete: false
  })
}

watch(tasks, (nouvelleValeur) => {
  localStorage.setItem('tasks', JSON.stringify(nouvelleValeur))
}, { deep: true })

const filtreActuel = ref('Toutes')

const filtreChange = (newFilter) => {
  filtreActuel.value = newFilter
}

const filteredTasks = computed(() => {
  switch (filtreActuel.value) {
    case 'Fait':
      return tasks.value.filter(task => task.isComplete)
    case 'A faire':
      return tasks.value.filter(task => !task.isComplete)
    default:
      return tasks.value
  }
})

const deleteTask = (task) => {
  const idTaskDelete = task.id
  tasks.value = tasks.value.filter(task => task.id !== idTaskDelete)
  localStorage.setItem('tasks', JSON.stringify(tasks.value))
}

</script>

<template>
  <div class="max-w-md mx-auto bg-white shadow-lg rounded-lg overflow-hidden mt-16">
    <div class="px-4 py-2 items-center text-center">
      <h1 class="text-gray-800 font-bold text-2xl uppercase">To-Do List</h1>
    </div>
    
    <Compteur :tasks="tasks" />

    <FilterTasks @filtreButtonPressed="filtreChange" />
    
    <FormTask @addTask="addTask" />
    
    <ul class="divide-y divide-gray-200 px-4">
      <TaskItem v-for="task in filteredTasks" :key="task.id" :task="task" @deleteTask="deleteTask" />
    </ul>
</div>
  <div>
    
  </div>
</template>
