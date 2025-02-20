<script setup lang="ts">
import Header from "./components/header.vue";
import CreateModal from "./components/createModal.vue";
import { ref } from "vue";

const showModal = ref(false);
</script>

<template>
  <Header @openModal="showModal = true" />
  <Transition>
    <CreateModal @closeModal="showModal = false" v-if="showModal" />
  </Transition>
</template>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: all 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
  transform: translateY(50px);
}
</style>
