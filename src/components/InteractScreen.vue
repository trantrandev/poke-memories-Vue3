<template>
  <h1>Interact Component here</h1>
  <card-flip
    v-for="(card, index) in cardsContext"
    :key="index"
    :imgBackFaceUrl="`images/${card}.png`"
  />
</template>

<script>
import CardFlip from "./Card";

export default {
  props: {
    cardsContext: {
      type: Array,
      default: function() {
        return [];
      }
    }
  },
  name: "InteractScreen",
  components: {
    CardFlip
  }
};
</script>

<style scoped>

</style>