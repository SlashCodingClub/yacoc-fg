<template>
  <div class="bg-gray-700 rounded-lg p-4">
    <div class="flex justify-between mb-2">
      <button class="bg-gray-600 px-2 py-1 rounded">Skill</button>
      <button class="bg-gray-600 px-2 py-1 rounded">Items</button>
    </div>
    <div class="grid grid-cols-5 gap-2">
      <button
        v-for="i in 40"
        :key="i"
        class="bg-gray-600 text-sm p-2 rounded border border-dashed border-gray-500"
      >
        {{ i }}
      </button>
    </div>
  </div>
</template>
