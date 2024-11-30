<template>
  <div class="bg-gray-800 text-white p-6 rounded-lg shadow-lg space-y-6">
    <!-- Scene Title and Description -->
    <div>
      <h2 class="text-2xl font-bold">🚂 Train</h2>
      <p class="text-gray-400">Abandoned Train, every seat is covered with dust</p>
    </div>

    <!-- Interaction Section -->
    <div class="space-y-4">
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

      <!-- NPC Section -->
      <div>
        <h3 class="text-lg font-semibold">👥 NPC</h3>
        <div class="flex space-x-4 mt-2">
          <!-- NPC Buttons -->
          <div v-for="(npc, index) in npcs" :key="index" class="relative group">
            <button
              @click="selectNpc(npc)"
              class="w-12 h-12 bg-gray-700 rounded-lg flex items-center justify-center hover:bg-gray-600"
            >
              <span class="text-2xl">{{ npc.icon }}</span>
            </button>
            <!-- Tooltip -->
            <span
              class="absolute bottom-full left-1/2 transform -translate-x-1/2 mb-2 px-2 py-1 text-sm text-black bg-white rounded opacity-0 group-hover:opacity-100 transition-opacity"
            >
              {{ npc.name }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { name: 'Box', icon: '📦', description: 'A dusty old box.' },
        { name: 'Spider', icon: '🕷️', description: 'A small but scary spider.' },
      ],
      npcs: [{ name: 'Monkey NPC', icon: '🐵', description: 'A playful monkey NPC.' }],
    }
  },
  methods: {
    selectItem(item) {
      this.$emit('select', item) // Emit selected item to the parent
    },
    selectNpc(npc) {
      this.$emit('select', npc) // Emit selected NPC to the parent
    },
  },
}
</script>
