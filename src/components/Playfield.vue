<template>
  <div class="playfield">
    <h2 class="playfield__header">Simon Says</h2>
    <div class="container">
      <Board @sounds="sounds" 
        :mutableIsStarted="mutableIsStarted"
      />
      <DashBoard
        @gameIsStarted="audio"
        :newRound="newRound"      
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
      sequence: [],
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
      return Math.floor((Math.random() * 4) + 1);
    },
    animate() {
      let animateSequence = this.sequence;
      let i = 0;
          const interval = setInterval(
              function() {
                console.log(animateSequence[i]);
                i++;

                if (i >= animateSequence.length) {
                  clearInterval(interval)
                }
              },600)
    },
    newRound() {
      let animateSequence = this.sequence;
      animateSequence.push(this.randomizeNumbers());
      this.animate(animateSequence)
    },
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
