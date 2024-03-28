<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  task: Object
})

const emit = defineEmits(['deleteTask'])

const deleteTask = () => {
  emit('deleteTask', props.task)
}

</script>

<template>
  <li class="py-4">
            <div class="flex items-center">
                <input :id="'todo-' + task.id" name="todo1" type="checkbox" class="h-4 w-4 text-teal-600 focus:ring-teal-500 border-gray-300 rounded" v-model="task.isComplete">
                <label :for="'todo-' + task.id" class="ml-3 block text-gray-900" >
                    <span class="text-lg font-medium" :class="{ completed: task.isComplete }">{{ task.task }}</span>
                </label>
                <button @click="deleteTask">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-red-600 hover:text-red-900" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
        </li>
</template>

<style>
.completed {
  text-decoration: line-through;
}
</style>
