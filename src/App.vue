<template>
  <div class="grid grid-cols-12 grid-rows-6 h-screen gap-2 p-4 bg-gray-800 text-gray-200">
    <!-- Enemy or Entity Info -->
    <EnemyInfo class="col-span-4 row-span-3" />

    <!-- Main Game Scene -->
    <MainGameScene class="col-span-4 row-span-3" />

    <!-- Player Info -->
    <PlayerInfo class="col-span-4 row-span-3" />

    <!-- Dice and Total -->
    <DiceSection class="col-span-2 row-span-3" />

    <!-- Chat and Event Log -->
    <ChatLog class="col-span-8 row-span-3" />

    <!-- Skill and Items -->
    <SkillAndItems class="col-span-2 row-span-3" />
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
}
</script>
