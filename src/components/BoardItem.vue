<template>
  <li :class="{ active: isActive }" @click="click" :sound="sound"></li>
</template>

<script>
export default {
  props: ['sound', 'mutableIsStarted'],
  data() {
    return {
      isActive: false,
    };
  },
  methods: {
    click() {
      if (!this.mutableIsStarted) {
        return
      } else {
        this.sound.play();
        this.isActive = !this.isActive;
        setTimeout(() => (this.isActive = false)), 2000;
      }
    },
  },
};
</script>
