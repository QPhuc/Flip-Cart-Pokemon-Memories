<template>
  <div class="screen">
    <h1>Poke Memories</h1>
    <p>Select mode to start game</p>
    <div class="modes">
      <button @click="onStart(16)">
        <span>4x4</span>
        <span>Easy</span>
      </button>
      <button @click="onStart(36)">
        <span>6x6</span>
        <span>Normal</span>
      </button>
      <button @click="onStart(64)">
        <span>8x8</span>
        <span>Hard</span>
      </button>
      <!-- <button @click="onStart(100)">
        <span>10x10</span>
        <span>Super Hard</span>
      </button> -->
    </div>
  </div>
</template>

<script>
export default {
  emits: ["onStart"],
  methods: {
    onStart(totalOfBlocks) {
      this.$emit("onStart", { totalOfBlocks });
    },
  },
};
</script>

<style lang="css" scoped>
.screen {
  width: 100%;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  background-color: var(--dark);
  color: var(--light);
}

.screen h1 {
  font-size: 4.5rem;
  text-transform: uppercase;
}

.screen p {
  font-size: 32px;
}

.modes {
  display: flex;
  margin-top: 2rem;
}

.modes button {
  font: var(--font);
  width: 150px;
  height: 150px;
  background: transparent;
  box-shadow: none;
  border: 1px solid var(--light);
  color: var(--light);
  display: flex;
  flex-direction: column;
  border-radius: 1rem;
  margin: 0 1rem;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background 0.3s ease-in-out;
}

.modes button:hover {
  background-color: var(--light);
  color: var(--dark);
}

.modes button span:first-child {
  font-size: 2rem;
}

.modes button span:last-child {
  display: block;
  font-size: 1.25rem;
  margin-top: 0.5rem;
}

@media (max-width: 739px) {
  .screen h1 {
    font-size: 2.5rem;
  }

  .screen p {
    font-size: 16px;
  }

  .modes {
    margin-top: 1rem;
  }
  .modes button {
    width: 50px;
    height: 50px;
    margin: 0 0.5rem;
  }

  .modes button span:first-child {
    font-size: 1rem;
  }

  .modes button span:last-child {
    font-size: 0.5rem;
  }
}
</style>
