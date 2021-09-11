<template>
  <div class="playfield">
    <h2 class="playfield__header">Simon Says</h2>
    <div class="container">
      <Board 
        :soundsArray="soundsArray" 
        :mutableIsStarted="mutableIsStarted"
        :sound='sound'
      />
      <DashBoard
        @gameIsStarted="audio"
        :animate="animate"      
      />
    </div>
  </div>
</template>

<script>
import Board from './Board.vue';
import DashBoard from './DashBoard.vue';

const sound1 = new Audio(require('../assets/sounds/1.mp3'));
const sound2 = new Audio(require('../assets/sounds/2.mp3'));
const sound3 = new Audio(require('../assets/sounds/3.mp3'));
const sound4 = new Audio(require('../assets/sounds/4.mp3'));

export default {
  props: {
    isStarted: {
      default: false,
      type: Boolean,
    },
    sound: {
      default: ''
    }
  },
  data() {
    return {
      soundsArray: [
        { color: 'red', sound: sound1, index: 1 },
        { color: 'blue', sound: sound2, index: 2 },
        { color: 'yellow', sound: sound3, index: 3 },
        { color: 'green', sound: sound4, index: 4 },
      ],
      mutableIsStarted: this.isStarted || false,
      sequence: [],
      animateSequence: [],
      start: 0,
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
      return(this.soundsArray[Math.floor((Math.random() * this.soundsArray.length))]);
    },
    randomSounds() {
      const random = this.randomizeNumbers()
      this.animateSequence.push(random);
    },
    newRound() {
    },
    playSound(sound) {
      sound.play()
    },
    animate() {
      this.randomSounds()
      const finish = this.animateSequence.length;

      // this.playSound(animateSequence.sound)
      let interval = setInterval(() => {
        // console.log(animateSequence[this.start]);
        
        if(this.start === finish) {
			
          console.log('that is all');
          clearInterval(interval)
          
        } else {
          this.randomSounds()
          this.animateSequence[this.start].sound.play();
          // console.log(animateSequence);
          this.start++
          // console.log(this.start);
        }
      }, 2000)
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
