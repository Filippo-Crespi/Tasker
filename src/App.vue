<script setup lang="ts">
import Header from "./components/header.vue";
import CreateModal from "./components/createModal.vue";
import Todo from "./components/Todo.vue";
import { ref, watch } from "vue";
const showModal = ref(false);

type Task = {
  title: string | undefined;
  description: string | undefined;
  date: Date | undefined;
  color: string | undefined;
  completed: boolean | undefined;
};

const tasks = ref<Task[]>([]);
const addTask = (task: Task) => {
  tasks.value.push(task);
};
const deleteTask = (id: number) => {
  tasks.value[id].completed = true;
};

let completed = ref<Task[]>([]);

let uncompleted = ref<Task[]>([]);

watch(tasks.value, (newTask) => {
  uncompleted.value = newTask.filter((element) => {
    return !element.completed;
  });
  completed.value = newTask.filter((element) => {
    return element.completed;
  });
});

for (let i = 0; i < 10; i++) {
  addTask({
    title: `Task ${i + 1}`,
    description: `Description for task ${i + 1}`,
    date: new Date(),
    color: `${Math.floor(Math.random() * 16777215)
      .toString(16)
      .padStart(6, "0")}`,
    completed: false,
  });
}
</script>

<template>
  <Header @openModal="showModal = true" />
  <Transition name="modal">
    <CreateModal @create-task="addTask" @closeModal="showModal = false" v-if="showModal" />
  </Transition>
  <div class="todo-box">
    <TransitionGroup name="todo">
      <div class="todo-group" v-for="(task, index) in uncompleted" :key="index">
        <button @click="deleteTask(index)">🗑️</button>
        {{ index }}
        <Todo
          :title="task.title"
          :color="task.color"
          :description="task.description"
          :date="task.date" />
      </div>
    </TransitionGroup>
  </div>
  <h2>Completed</h2>
  <div class="todo-box">
    <TransitionGroup name="todo">
      <Todo
        v-for="(task, index) in completed"
        :key="index"
        :title="task.title"
        :color="task.color"
        :description="task.description"
        :date="task.date" />
    </TransitionGroup>
  </div>
</template>

<style scoped>
.modal-enter-active,
.modal-leave-active {
  transition: all 0.5s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: translateY(50px);
}

.todo-box {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 2rem;
}

.todo-group {
  display: flex;
  gap: 12px;
}

.todo-enter-active,
.todo-leave-active {
  transition: all 0.5s ease;
}
.todo-enter-from,
.todo-leave-to {
  opacity: 0;
  transform: translateX(-30px);
}
</style>
