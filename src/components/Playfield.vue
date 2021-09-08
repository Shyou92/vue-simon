<template>
  <div class="playfield">
    <h2 class="playfield__header">Simon Says</h2>
    <div class="container">
      <Board @sounds="sounds" />
      <DashBoard @gameIsStarted="audio"
      />
    </div>
  </div>
</template>

<script>
import Board from './Board.vue';
import DashBoard from './DashBoard.vue';

export default {
  props: ['isStarted'],
  data() {
    return {
      sounds: [],
      mutableIsStarted: this.isStarted,
    }
  },
  components: {
    Board,
    DashBoard,
  },
  methods: {
    audio(isStarted) {
      this.mutableIsStarted = isStarted;
      console.log(this.mutableIsStarted);
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
