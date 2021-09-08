<template>
  <li :class="{ active: isActive }" @click="click" :sounds="sounds"></li>
</template>

<script>
export default {
  props: {
    sounds: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      isActive: false,
    };
  },
  methods: {
    click() {
      console.log(sounds);
      sound.play();
      this.isActive = !this.isActive;
      setTimeout(() => (this.isActive = false)), 2000;
    },
  },
};
</script>
