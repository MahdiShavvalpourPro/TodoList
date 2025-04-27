<script setup>
import TaskForm from "./components/TaskForm.vue";
import TaskList from "./components/TaskList.vue";
import { onMounted, provide, reactive } from "vue";

onMounted(() => {
  const savedTasks = JSON.parse(localStorage.getItem("tasks"));
  if (savedTasks) {
    console.log(savedTasks);
    tasks.push(...savedTasks);
  }
});
let tasks = reactive([]);

function addTask(task) {
  tasks.push({
    text: task,
    completed: false,
  });
  // console.log(tasks);
  localStorage.setItem("tasks", JSON.stringify(tasks));
}
function removeTask(index) {
  tasks.splice(index, 1);
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

function toggleTaskStatus(index) {
  tasks[index].completed = !tasks[index].completed;
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

provide("removeTask", removeTask);
provide("toggleTaskStatus", toggleTaskStatus);
</script>
<template>
  <div class="app-container">
    <h1>لیست تسک های من</h1>
    <TaskForm @add-Task="addTask" />
    <TaskList v-bind:tasks="tasks" />
  </div>
</template>


<style>
.app-container {
  max-width: 400px;
  margin: 40px auto;
  background: #f9f9f9;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  text-align: center;
  max-height: 490px;
  overflow: auto;
}
h1 {
  font-size: 24px;
  color: #333;
  margin-bottom: 1rem;
}
</style>
