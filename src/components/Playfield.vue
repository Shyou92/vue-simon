<template>
  <div class="playfield">
    <h2 class="playfield__header">Simon Says</h2>
    <div class="container">
      <Board @sounds="sounds" 
        :mutableIsStarted="mutableIsStarted"
      />
      <DashBoard @gameIsStarted="audio"
      />
    </div>
  </div>
</template>

<script>
import Board from './Board.vue';
import DashBoard from './DashBoard.vue';

export default {
  props: {
    isStarted: {
      default: false,
      type: Boolean,
    }
  },
  data() {
    return {
      sounds: [],
      mutableIsStarted: this.isStarted || false,
    }
  },
  components: {
    Board,
    DashBoard,
  },
  methods: {
    audio(isStarted) {
      this.mutableIsStarted = isStarted;
    },
    randomizeNumbers() {
      return Math.floor((Math.random() * sounds.length) + 1);
    }
  }
};
</script>
<style scoped>
.playfield {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.container {
  display: flex;
}
</style>
