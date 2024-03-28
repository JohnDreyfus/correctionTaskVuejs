<script setup>
const emit = defineEmits(['filtreButtonPressed'])

const filtre = (newFilter) => {
  emit('filtreButtonPressed', newFilter)
}

</script>

<template>
    <div class="px-4 py-2 flex justify-center">
      <div class="flex space-x-2">
        <div class="flex w-full justify-center rounded-md bg-indigo-600 px-2 py-1 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">
          <button @click="filtre('Toutes')">Toutes</button>
        </div>
        <div class="flex w-full justify-center rounded-md bg-indigo-600 px-2 py-1 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">
          <button @click="filtre('Fait')">Fait</button>
        </div>
        <div class="flex w-full justify-center rounded-md bg-indigo-600 px-2 py-1 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">
          <button @click="filtre('A faire')">A faire</button>
        </div>
      </div>
    </div>
</template>