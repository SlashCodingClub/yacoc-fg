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
  props: {
    min: {
      type: Number,
      default: 1, // Default minimum dice value
    },
    max: {
      type: Number,
      default: 20, // Default maximum dice value
    },
  },
  setup(props) {
    const diceNumber = ref(props.min) // Current dice number starts at the minimum
    const isRolling = ref(false) // Prevent multiple rolls
    const total = ref(0) // Store the final result

    const rollDice = () => {
      if (isRolling.value) return

      isRolling.value = true

      const finalNumber = Math.floor(Math.random() * (props.max - props.min + 1)) + props.min // Final result within bounds
      let currentNumber = Math.floor(Math.random() * (props.max - props.min + 1)) + props.min // Initial random number
      let iterations = 0 // Track iterations
      let currentSpeed = 50 // Initial speed
      let range = props.max - props.min // Start with full range

      const roll = () => {
        // Gradually reduce the range and move toward the finalNumber
        if (iterations >= 10) {
          diceNumber.value = finalNumber // Set final number
          total.value = finalNumber
          isRolling.value = false
          return
        }

        // Generate a number closer to the final result
        const direction = finalNumber > currentNumber ? 1 : -1 // Determine the direction
        currentNumber += direction * Math.floor(Math.random() * Math.ceil(range / 4))

        // Ensure the number stays within bounds
        if (currentNumber > props.max) currentNumber = props.max
        if (currentNumber < props.min) currentNumber = props.min

        diceNumber.value = currentNumber
        range = Math.max(1, range - 2) // Narrow down the range
        currentSpeed += 20 // Slow down the speed

        iterations++
        setTimeout(roll, currentSpeed)
      }

      roll() // Start the dice roll
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
button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
