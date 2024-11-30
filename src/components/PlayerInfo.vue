<template>
  <div class="bg-gray-5 rounded-lg shadow-lg p-6 flex items-center space-x-6">
    <!-- Avatar Section -->
    <div class="w-20 h-20 bg-yellow-300 rounded-full flex items-center justify-center text-6xl">
      🧔
    </div>

    <!-- Info Section -->
    <div class="flex-grow">
      <!-- Player Name -->
      <div class="text-xl font-bold mb-2">Name: Mr. Wang</div>

      <!-- Status Section -->
      <div class="space-y-2">
        <div class="flex items-center">
          <span class="w-20 font-medium">Status</span>
          <div class="flex-grow bg-gray-300 h-4 rounded">
            <div
              class="bg-green-500 h-full rounded"
              :style="{ width: statusPercentage + '%' }"
            ></div>
          </div>
          <span class="ml-3 text-sm">{{ status }}</span>
        </div>

        <div class="flex items-center">
          <span class="w-20 font-medium">HP:</span>
          <div class="flex-grow bg-gray-300 h-4 rounded">
            <div class="bg-red-500 h-full rounded" :style="{ width: hpPercentage + '%' }"></div>
          </div>
          <span class="ml-3 text-sm">{{ hp }}</span>
        </div>

        <div class="flex items-center">
          <span class="w-20 font-medium">San:</span>
          <div class="flex-grow bg-gray-300 h-4 rounded">
            <div class="bg-blue-500 h-full rounded" :style="{ width: sanPercentage + '%' }"></div>
          </div>
          <span class="ml-3 text-sm">{{ san }}</span>
        </div>
      </div>
    </div>

    <!-- Ability Stats -->
    <div class="text-right space-y-2">
      <div class="text-lg font-semibold">Ability Stats</div>
      <div class="text-sm">Power: {{ power }}</div>
      <div class="text-sm">Wisdom: {{ wisdom }}</div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    // Example data (can be props or come from a backend)
    const status = ref(75) // Current status value
    const hp = ref(50) // Current HP value
    const san = ref(60) // Current SAN value
    const power = ref(80) // Power stat
    const wisdom = ref(90) // Wisdom stat

    // Calculating percentages for status bars
    const statusPercentage = ref((status.value / 100) * 100)
    const hpPercentage = ref((hp.value / 100) * 100)
    const sanPercentage = ref((san.value / 100) * 100)

    return {
      status,
      hp,
      san,
      power,
      wisdom,
      statusPercentage,
      hpPercentage,
      sanPercentage,
    }
  },
}
</script>

<style scoped>
/* Add any additional styling here if needed */
</style>
