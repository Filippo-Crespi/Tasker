<template>
  <div class="blur">
    <div class="modal">
      <span class="title">New Task</span>
      <Divider />
      <FloatLabel variant="in">
        <label for="task-title">Title</label>
        <InputText id="task-title" v-model="task.title" />
      </FloatLabel>
      <FloatLabel variant="in">
        <label for="task-text">Description</label>
        <Textarea id="task-text" style="resize: none" rows="10" v-model="task.description" />
      </FloatLabel>
      <FloatLabel variant="in">
        <label for="task-date">Date</label>
        <DatePicker id="task-date" date-format="dd/mm/yy" show-button-bar v-model="task.date" />
      </FloatLabel>
      <div class="color-box">
        <ColorPicker id="task-color" v-model="task.color" />
      </div>
      <button @click="createTask()">Create</button>
      <button @click="$emit('closeModal')">Cancel</button>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { InputText, Textarea, FloatLabel, DatePicker, ColorPicker, Divider } from "primevue";
import { ref } from "vue";

type Task = {
  title: string | undefined;
  description: string | undefined;
  date: Date | undefined;
  color: string | undefined;
  completed: boolean | undefined;
};

const createTask = () => {
  // for (let field in task.value) {
  //   if (!task.value[field as keyof Task]) return;
  // }

  emit("closeModal");
  emit("createTask", task.value);
};

const emit = defineEmits(["createTask", "closeModal"]);
const task = ref<Task>({
  title: undefined,
  description: undefined,
  date: undefined,
  color: undefined,
  completed: false,
});
</script>

<style scoped>
.blur {
  width: 100vw;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  backdrop-filter: blur(10px);
}

.modal {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.color-box {
  display: flex;
  justify-content: center;
}

span.title {
  font-weight: 700;
  font-size: 3rem;
}
</style>
