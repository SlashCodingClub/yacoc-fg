<template>
  <div class="bg-gray-800 text-white p-6 rounded-lg shadow-lg flex flex-col h-full">
    <!-- Chat Log -->
    <div class="flex-grow overflow-y-auto space-y-4 bg-gray-700 p-4 rounded">
      <div v-for="(log, index) in chatLogs" :key="index" class="text-sm">
        <span class="font-bold">{{ log.sender }}:</span> {{ log.message }}
      </div>
    </div>

    <!-- Message Input -->
    <div class="mt-4 flex items-center space-x-4">
      <!-- Selected Item Button -->
      <button
        v-if="selected"
        @click="$emit('clear-selection')"
        class="flex items-center bg-gray-600 hover:bg-gray-500 px-4 py-2 rounded-lg space-x-2"
      >
        <span class="text-2xl">{{ selected.icon }}</span>
        <span>{{ selected.name }}</span>
      </button>

      <!-- Message Field -->
      <input
        v-model="message"
        type="text"
        placeholder="Type your message..."
        class="flex-grow bg-gray-700 text-gray-200 px-4 py-2 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500"
        @keyup.enter="sendMessage"
      />

      <!-- Send Button -->
      <button
        @click="sendMessage"
        class="bg-indigo-600 hover:bg-indigo-500 text-white px-4 py-2 rounded-lg"
      >
        Send
      </button>
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
  data() {
    return {
      chatLogs: [], // Array to hold chat log messages
      message: '', // Current message in the input field
    }
  },
  methods: {
    sendMessage() {
      if (this.message.trim()) {
        this.chatLogs.push({ sender: 'Player', message: this.message }) // Append to chat logs
        this.message = '' // Clear input field
      }
    },
  },
}
</script>

<style scoped>
/* Optional styles to tweak UI further */
</style>
