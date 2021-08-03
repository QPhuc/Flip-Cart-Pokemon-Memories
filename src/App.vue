<template>
  <div>
    <MainScreen v-if="statusMatch === 'default'" @onStart="onHandleBeforeStart($event)"/>
    <InteractScreen v-if="statusMatch === 'match'" :cardsContext="settings.cardsContext" />
  </div>
</template>

<script>
import MainScreen from './components/MainScreen.vue';
import InteractScreen from './components/InteractScreen.vue';

import { shuffled } from "./utils/array"
export default {
  name: 'App',
  data() {
    return {
      settings: {
        totalOfBlocks: 0,
        cardsContext: [],
        staredAt: null,
      },
      statusMatch: 'default',
    }
  },
  components: {
    MainScreen,
    InteractScreen
  },
  methods: {
    onHandleBeforeStart(configs) {
      this.settings.totalOfBlocks = configs.totalOfBlocks;
      const firstCards = Array.from( {length: this.settings.totalOfBlocks / 2}, (_, i) => i + 1 );
      const secondCards = [...firstCards];
      const cards = [...firstCards, ...secondCards];
      this.settings.cardsContext = shuffled(shuffled(shuffled(shuffled(cards))));
      this.settings.staredAt = new Date().getTime();

      // data ready
      this.statusMatch = "match";
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
