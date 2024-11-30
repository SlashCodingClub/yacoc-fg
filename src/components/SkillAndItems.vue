<template>
  <div class="bg-gray-800 text-white p-6 rounded-lg shadow-lg space-y-6">
    <!-- Skills Section -->
    <div>
      <h3 class="text-lg font-semibold">🎯 Skills</h3>
      <div class="flex space-x-4 mt-2">
        <!-- Skill Buttons -->
        <div v-for="(skill, index) in skills" :key="index" class="relative group">
          <button
            @click="selectSkill(skill)"
            class="w-12 h-12 bg-gray-700 rounded-lg flex items-center justify-center hover:bg-gray-600"
          >
            <span class="text-2xl">{{ skill.icon }}</span>
          </button>
          <!-- Tooltip -->
          <span
            class="absolute bottom-full left-1/2 transform -translate-x-1/2 mb-2 px-2 py-1 text-sm text-black bg-white rounded opacity-0 group-hover:opacity-100 transition-opacity"
          >
            {{ skill.name }}
          </span>
        </div>
      </div>
    </div>

    <!-- Items Section -->
    <div>
      <h3 class="text-lg font-semibold">📦 Items</h3>
      <div class="flex space-x-4 mt-2">
        <!-- Item Buttons -->
        <div v-for="(item, index) in items" :key="index" class="relative group">
          <button
            @click="selectItem(item)"
            class="w-12 h-12 bg-gray-700 rounded-lg flex items-center justify-center hover:bg-gray-600"
          >
            <span class="text-2xl">{{ item.icon }}</span>
          </button>
          <!-- Tooltip -->
          <span
            class="absolute bottom-full left-1/2 transform -translate-x-1/2 mb-2 px-2 py-1 text-sm text-black bg-white rounded opacity-0 group-hover:opacity-100 transition-opacity"
          >
            {{ item.name }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      skills: [
        { name: 'Fireball', icon: '🔥', description: 'Cast a powerful fireball.' },
        { name: 'Healing', icon: '💊', description: 'Restore HP to an ally.' },
      ],
      items: [
        { name: 'Potion', icon: '🧪', description: 'Restores 50 HP.' },
        { name: 'Sword', icon: '⚔️', description: 'A sharp blade to attack enemies.' },
      ],
    }
  },
  methods: {
    selectSkill(skill) {
      this.$emit('select', skill) // Emit selected skill to the parent
    },
    selectItem(item) {
      this.$emit('select', item) // Emit selected item to the parent
    },
  },
}
</script>
