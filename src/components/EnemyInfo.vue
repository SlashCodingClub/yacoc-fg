<template>
  <div class="p-4">
    <div v-if="selected" class="space-y-2">
      <h2 class="text-xl font-bold">{{ selected.icon + selected.name }}</h2>
      <p>{{ selected.description }}</p>
    </div>
    <div v-else class="text-gray-400">
      <p>Select an item or NPC to see details.</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    selected: {
      type: Object,
      default: null,
    },
  },
}
</script>
