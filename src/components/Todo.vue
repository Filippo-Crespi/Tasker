<script lang="ts" setup>
const props = defineProps({
  title: String,
  color: String,
  description: String,
  date: Date,
});
</script>

<template>
  <div class="todo">
    <div class="color" :style="`background-color: #${color}`"></div>
    <div class="data">
      <span class="title">{{ title }}</span>
      <span class="date">{{ date?.toDateString() }}</span>
      <span>{{ description }}</span>
    </div>
  </div>
</template>

<style scoped>
.todo {
  background-color: aliceblue;
  gap: 10px;
  display: flex;
  border-radius: 12px;
  width: 100%;
}

.color {
  width: 12px;
  border-radius: 12px 0 0 12px;
}

.data .title {
  font-weight: 600;
}

.data .date {
  font-weight: 300;
}

.data {
  display: flex;
  gap: 16px;
  padding: 1rem 0.5rem;
}
</style>
