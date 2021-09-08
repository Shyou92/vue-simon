<template>
  <li :class="{ active: isActive }" @click="click" :sound="sound"></li>
</template>

<script>
export default {
  props: ['sound'],
  data() {
    return {
      isActive: false,
    };
  },
  methods: {
    click() {
      if(this.isStarted === false) {
        return;
      }
      this.sound.play();
      this.isActive = !this.isActive;
      setTimeout(() => (this.isActive = false)), 2000;
    },
  },
};
</script>
