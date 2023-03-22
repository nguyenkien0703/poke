<template>
  <div class="screen">
    <h1>This is the game Pokemon</h1>
    <h3>Game is userful</h3>
    <div class="actions">
      <button @click="onStart(16)">
        <span>4*4</span>
        <span>Easy</span>
      </button>
      <button @click="onStart(36)">
        <span>6*6</span>
        <span>Medium</span>
      </button>
      <button @click="onStart(64)">
        <span>8*8</span>
        <span>Hard</span>
      </button>
      <button @click="onStart(100)">
        <span>10*10</span>
        <span>SuperHard</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    onStart(totalBlocks) {
      this.$emit("onStart", { totalBlocks });
    },
  },
};
</script>
