<template>
  <div class="grid grid-cols-12 grid-rows-6 h-screen gap-2 p-4 bg-gray-800 text-gray-200">
    <!-- Enemy or Entity Info -->
    <EnemyInfo class="col-span-4 row-span-3" :selected="selected" />

    <!-- Main Game Scene -->
    <MainGameScene class="col-span-4 row-span-3" @select="updateSelection" />

    <!-- Player Info -->
    <PlayerInfo class="col-span-4 row-span-3" />

    <!-- Dice and Total -->
    <DiceSection class="col-span-2 row-span-3" />

    <!-- Chat and Event Log -->
    <ChatLog class="col-span-8 row-span-3" :selected="selected" @clear-selection="clearSelected" />

    <!-- Skill and Items -->
    <SkillAndItems class="col-span-2 row-span-3" @select="updateSelection" />
  </div>
</template>

<script>
import EnemyInfo from './components/EnemyInfo.vue'
import MainGameScene from './components/MainGameScene.vue'
import PlayerInfo from './components/PlayerInfo.vue'
import DiceSection from './components/DiceSection.vue'
import ChatLog from './components/ChatLog.vue'
import SkillAndItems from './components/SkillAndItems.vue'

export default {
  components: {
    EnemyInfo,
    MainGameScene,
    PlayerInfo,
    DiceSection,
    ChatLog,
    SkillAndItems,
  },

  data() {
    return {
      selected: null, // Holds the current selected item or NPC
    }
  },

  methods: {
    updateSelection(selection) {
      this.selected = selection // Update the selected entity
    },
    clearSelected() {
      this.selected = null // Reset the selected item
    },
  },
}
</script>
