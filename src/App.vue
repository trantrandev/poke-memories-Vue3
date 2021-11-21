<template>
  <main-screen v-if="statusMatch === 'default'" @onStart="onHandleBeforeStart($event)"></main-screen>
  <interact-screen v-if="statusMatch === 'match'"></interact-screen>
</template>

<script>


import MainScreen from "./components/MainScreen";
import InteractScreen from "./components/InteractScreen";

export default {
  name: "App",
  data() {
    return {
      statusMatch: "default",
    };
  },
  components: {
    MainScreen,
    InteractScreen
  },
  methods: {
    onHandleBeforeStart(config) {
      console.log("onHandleBeforeStart", config);
      this.statusMatch = "match";
    }
  }
};
</script>
