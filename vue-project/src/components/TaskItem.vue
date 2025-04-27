<script setup>
import { inject } from "vue";
defineProps(["task", "index"]);
const removeTask = inject("removeTask");
const toggleTaskStatus = inject("toggleTaskStatus");
</script>
<template>
  <li class="task-item">
    <span
      v-bind:class="{ completed: task.completed }"
      @click="toggleTaskStatus(index)"
      >{{ task.text }}</span
    >
    <button @click="removeTask(index)">حذف</button>
  </li>
</template>

<style scoped>
.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  background: white;
  margin: 5px 0;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  font-size: 1.5rem;
}
.task-item span {
  cursor: pointer;
}
.task-item span.completed {
  text-decoration: line-through;
  color: gray;
}
.task-item button {
  background: #dc3545;
  color: white;
  border: none;
  padding: 5px;
  cursor: pointer;
  border-radius: 5px;
  font-size: 1rem;
}
.task-item button:hover {
  background: #c82333;
}

.task-item span {
  font-size: 1rem;
}
</style>

