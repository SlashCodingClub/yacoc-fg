<template>
  <div class="bg-gray-800 text-white p-6 rounded-lg shadow-lg flex flex-col h-full">
    <!-- Chat Log -->
    <div class="flex-grow overflow-y-auto space-y-4 bg-gray-700 p-4 rounded">
      <div v-for="(log, index) in chatLogs" :key="index" class="text-sm">
        <!-- Display Sender and Receiver -->
        <span class="font-bold">{{ log.sender }} → {{ log.receiver }}:</span> {{ log.message }}
      </div>
    </div>

    <!-- Message Input -->
    <div class="mt-4 flex items-center space-x-4">
      <!-- Selected Item Button -->
      <button
        v-if="selected"
        @click="clearSelected"
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
import axios from 'axios'

export default {
  props: {
    selected: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      message: '',
      chatLogs: [],
    }
  },
  mounted() {
    this.fetchRecentLogs()
  },
  methods: {
    async fetchRecentLogs() {
      try {
        // Calculate the timestamp 5 minutes ago
        // const fiveMinutesAgo = new Date(Date.now() - 5 * 60 * 1000).toISOString()

        // Send GET request to fetch game logs from the last 5 minutes
        // const response = await axios.get('http://localhost:3000/messages', {
        //   params: {
        //     start_time: fiveMinutesAgo, // Pass the timestamp as query parameter
        //   },
        // })
        const response = await axios.get('http://localhost:3000/messages')

        // Assuming response.data contains an array of logs
        this.chatLogs = response.data
      } catch (error) {
        console.error('Error fetching recent logs:', error)
      }
    },

    async sendMessage() {
      if (this.message.trim()) {
        const timestamp = new Date().toISOString() // Get current timestamp
        const receiver = this.selected ? this.selected.name : 'None'
        const gameLog = {
          sender: 'Hero_250', // Example player name, replace with dynamic data if necessary
          receiver: receiver, // Selected item name as receiver
          timestamp,
          action_message: this.message.trim(), // Message from the input field
        }
        try {
          // Send the message to the backend via POST request
          await axios.post('http://localhost:3000/messages', { game_log: gameLog })

          // If successful, push the message to the chat log
          this.chatLogs.push({
            sender: gameLog.sender,
            receiver: gameLog.receiver, // Ensure the receiver is included in the log
            timestamp: gameLog.timestamp, // Include timestamp
            message: this.message,
          })

          this.message = '' // Clear input field
        } catch (error) {
          console.error('Error sending message to the backend:', error)
          // Optionally handle the error (e.g., show a message to the user)
        }
      }
    },
  },
}
</script>

<style scoped>
/* Optional styles to tweak UI further */
</style>
