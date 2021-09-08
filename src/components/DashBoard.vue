<template>
  <div class="dashboard">
    <h3 class="dashboard__header">Round: 0</h3>
    <button class="dashboard__start">Start</button>
    <ul class="dashboard__list">
      Game options:
      <li class="dashboard__list-item">
        <input type="radio" name="" id="normal" />
        <label for="normal">Normal</label>
      </li>
      <li class="dashboard__list-item">
        <input type="radio" name="" id="sound" />
        <label for="sound">Sounds Only</label>
      </li>
      <li class="dashboard__list-item">
        <input type="radio" name="" id="light" />
        <label for="light">Light Only</label>
      </li>
      <li class="dashboard__list-item">
        <input type="radio" name="" id="free" />
        <label for="free">Free Board</label>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.dashboard {
  margin-left: 350px;
}
</style>
