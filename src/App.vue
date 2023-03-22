<template>
  <main-screen
    v-if="statusMatch === 'default'"
    @onStart="onHandleBeforeStart($event)"
  />
  <interact-sreen
    v-if="statusMatch === 'match'"
    :cardsContext="settings.cardsContext"
  />
</template>

<script>
import MainScreen from "./components/MainScreen.vue";
import InteractSreen from "./components/InteractSreen.vue";
import { shuffed } from "./utils/array";
export default {
  name: "App",
  data() {
    return {
      settings: {
        totalBlocks: 0,
        cardsContext: [],
        startedAt: null,
      },
      statusMatch: "default",
    };
  },
  components: {
    MainScreen,
    InteractSreen,
  },
  methods: {
    onHandleBeforeStart(config) {
      this.settings.totalBlocks = config.totalBlocks;
      const firstCards = Array.from(
        { length: this.settings.totalBlocks / 2 },
        (_, i) => i + 1
      );
      const secondCards = [...firstCards];
      const cards = [...secondCards, ...firstCards];
      this.settings.cardsContext = shuffed(shuffed(shuffed(shuffed(cards))));
      this.settings.startedAt = new Date().getTime();
      // data ready
      this.statusMatch = "match";
    },
  },
};
</script>
