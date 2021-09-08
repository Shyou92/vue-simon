<template>
  <div class="playfield">
    <h2 class="playfield__header">Simon Says</h2>
    <div class="container">
      <Board />
      <DashBoard />
    </div>
  </div>
</template>

<script>
import Board from './Board.vue';
import DashBoard from './DashBoard.vue';

export default {
  components: {
    Board,
    DashBoard,
  },
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
