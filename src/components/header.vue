<template>
  <header>
    <div class="logo-box">
      <img src="../assets/vue.svg" alt="" />
      <span class="title">Tasker</span>
    </div>
    <div>
      <button @click="$emit('openModal')"><span>+</span> Create Task</button>
    </div>
  </header>
</template>

<script lang="ts" setup></script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.title {
  font-size: 2rem;
  font-weight: 600;
}

.logo-box {
  display: flex;
  align-items: center;
  gap: 12px;
}

button {
  display: flex;
  gap: 8px;
  align-items: center;
}

button span {
  font-weight: bolder;
}
</style>
