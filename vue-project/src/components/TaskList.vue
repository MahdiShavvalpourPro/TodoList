<script setup>
import TaskItem from "./TaskItem.vue";
defineProps(["tasks"]);
</script>
<template>
  <ul class="task-list">
    <TaskItem
      v-for="(task, index) in tasks"
      v-bind:key="index"
      v-bind:task="task"
      :index="index"
    />
  </ul>
</template>

<style scoped>
.task-list {
  list-style: none;
  padding: 0;
}
</style>
