<template>
  <div class="bg-gray-700 rounded-lg p-4 text-center flex flex-col items-center">
    <div class="text-6xl font-bold mb-4">{{ diceNumber }}</div>
    <button
      class="bg-gray-600 px-4 py-2 rounded text-gray-200"
      @click="rollDice"
      :disabled="isRolling"
    >
      {{ isRolling ? 'Rolling...' : 'Roll Dice' }}
    </button>
    <p class="mt-4">Total: {{ total }}</p>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const diceNumber = ref(1) // Current dice number
    const isRolling = ref(false) // Flag to prevent multiple rolls
    const total = ref(0) // Total value of dice rolls

    const rollDice = () => {
      if (isRolling.value) return

      isRolling.value = true
      const finalNumber = Math.floor(Math.random() * 20) + 1 // Generate random number (1-20)
      let currentSpeed = 50 // Initial speed in milliseconds
      let iterations = 0 // Track how many times the number has changed

      const rollInterval = setInterval(() => {
        diceNumber.value = Math.floor(Math.random() * 20) + 1

        iterations++
        currentSpeed += 20 // Gradually slow down the speed
        if (iterations >= 10) {
          clearInterval(rollInterval)
          diceNumber.value = finalNumber // Set the final dice number
          isRolling.value = false
          total.value = finalNumber
        }
      }, currentSpeed)
    }

    return {
      diceNumber,
      isRolling,
      total,
      rollDice,
    }
  },
}
</script>

<style>
/* Optional: Add custom styles for dice animation */
button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
