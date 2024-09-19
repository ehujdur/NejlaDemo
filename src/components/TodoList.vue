<template>
  <div class="todo-list">
    <input
      v-model="newTask"
      @keyup.enter="addTask"
      placeholder="Add a new task..."
    />
    <ul>
      <TodoItem
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @toggle-complete="toggleTaskComplete"
        @delete-task="deleteTask"
      />
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TodoItem from './TodoItem.vue';

const newTask = ref('');
const tasks = ref([
  { id: 1, text: 'Learn Vue 3', completed: false },
  { id: 2, text: 'Build a project', completed: false },
]);

const addTask = () => {
  if (newTask.value.trim() === '') return;
  tasks.value.push({
    id: Date.now(),
    text: newTask.value,
    completed: false,
  });
  newTask.value = '';
};

const deleteTask = (id) => {
  tasks.value = tasks.value.filter((task) => task.id !== id);
};

const toggleTaskComplete = (id) => {
  console.log('before:', tasks.value);
  const task = tasks.value.find((task) => task.id === id);
  console.log(task);
  if (task) {
    task.completed = !task.completed;
  }
  console.log('after:', tasks.value);
};
</script>

<style scoped>
.todo-list {
  max-width: 400px;
  margin: 0 auto;
  text-align: left;
}

input {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
}

ul {
  list-style-type: none;
  padding: 0;
}
</style>
