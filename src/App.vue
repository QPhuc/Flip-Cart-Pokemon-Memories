<template>
  <div>
    <MainScreen v-if="statusMatch === 'default'" @onStart="onHandleBeforeStart($event)"/>
    <InteractScreen v-if="statusMatch === 'match'"/>
  </div>
</template>

<script>
import MainScreen from './components/MainScreen.vue'
import InteractScreen from './components/InteractScreen.vue'
export default {
  name: 'App',
  data() {
    return {
      statusMatch: 'default'
    }
  },
  components: {
    MainScreen,
    InteractScreen
  },
  methods: {
    onHandleBeforeStart(config) {
      console.log("running handle", config);
      this.statusMatch = "match"
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
