<template>
  <div class="blur">
    <div class="modal">
      <h1>New Task</h1>
      <div class="input-box">
        <label for="task-title">Title</label>
        <input type="text" id="task-title" />
      </div>
      <div class="input-box">
        <label for="task-text">Text</label>
        <textarea type="text" id="task-text" />
      </div>
      <div class="input-box">
        <label for="task-text">Date</label>
        <input type="date" id="task-date" />
      </div>
      <div class="input-box">
        <label for="task-color">Color</label>
        <select name="task-color" id="task-color">
          <option value="red">Red</option>
          <option value="blue">Blue</option>
          <option value="green">Green</option>
          <option value="yellow">Yellow</option>
          <option value="purple">Purple</option>
          <option value="orange">Orange</option>
          <option value="pink">Pink</option>
        </select>
      </div>
      <button>Create</button>
      <button @click="$emit('closeModal')">Cancel</button>
    </div>
  </div>
</template>

<script lang="ts" setup></script>

<style scoped>
.blur {
  width: 100vw;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  backdrop-filter: blur(10px);
}
textarea {
  resize: none;
  height: 8rem;
  padding-right: 0;
}

.modal {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 0 3rem;
}

.input-box {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

input,
select,
textarea {
  background-color: #f5f5f5;
  border: none;
  outline: none;
  padding: 0.8rem 1.6rem;
}
</style>
