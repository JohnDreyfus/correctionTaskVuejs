<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  tasks: Array
})
</script>

<template>
    <div class="px-4 py-2 flex justify-center">
      <div class="flex">
        <div class="text-gray-800 font-bold text-lg mb-2 mr-4">
          Fait: {{ tasks.filter(task => task.isComplete).length }}
        </div>
        <div class="text-gray-800 font-bold text-lg mb-2">
          A faire: {{ tasks.filter(task => !task.isComplete).length }}
        </div>
      </div>
    </div>
</template>