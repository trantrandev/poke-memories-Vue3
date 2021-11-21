<template>
  <main-screen v-if="statusMatch === 'default'" @onStart="onHandleBeforeStart($event)"></main-screen>
  <interact-screen
    v-if="statusMatch === 'match'"
    :cardsContext="settings.cardsContext">
  </interact-screen>
</template>

<script>


import MainScreen from "./components/MainScreen";
import InteractScreen from "./components/InteractScreen";
import { shuffle } from "./utils/array";

export default {
  name: "App",
  data() {
    return {
      statusMatch: "default",
      settings: {
        totalOfBlocks: 0,
        cardsContext: "",
        startedAt: null
      }
    };
  },
  components: {
    MainScreen,
    InteractScreen
  },
  methods: {
    onHandleBeforeStart(config) {
      this.settings.totalOfBlocks = config.totalOfBlocks;
      const firstCards = Array.from(
        { length: this.settings.totalOfBlocks / 2 },
        (_, i) => i + 1
      );
      //copy array from firstCards use syntax ES6
      const secondCards = [...firstCards];
      const cards = [...firstCards, ...secondCards];
      this.settings.cardsContext = shuffle(
        shuffle(shuffle((shuffle(cards))))
      );
      this.settings.startedAt = new Date().getTime();//Data ready

      this.statusMatch = "match";
    }
  }
};
</script>
