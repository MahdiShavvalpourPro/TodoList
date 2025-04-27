<script setup>
import { ref } from "vue";

const newTask = ref("");
const emit = defineEmits(["add-Task"]);
</script>
<template>
  <form
    @submit.prevent="
      emit('add-Task', newTask);
      newTask = '';
    "
    class="task-form"
  >
    <input v-model="newTask" placeholder="لطفا تسک جدید را وارد کنید" />
    <button :disabled="!newTask" type="submit">اضافه کردن</button>
    <!-- <p>{{ newTask }}</p> -->
  </form>
</template>

<style scoped>
.task-form {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}
.task-form input {
  flex: 1;
  padding: 8px;
  border: 2px solid #ddd;
  border-radius: 5px;
  font-family: "yekan bakh light", sans-serif;
}
.task-form button {
  background: #28a745;
  color: white;
  border: none;
  padding: 8px 15px;
  cursor: pointer;
  border-radius: 5px;
  font-family: "yekan bakh light";
}
.task-form button:hover {
  background: #218838;
}
</style>