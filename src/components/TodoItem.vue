<template>
  <li :class="{ completed: task.completed }">
    <input type="checkbox" @change="toggleComplete" />
    <span>{{ task.text }}</span>
    <button @click="deleteTask">Delete</button>
  </li>
</template>

<script setup>
  const props = defineProps({
    task: Object,
  });

  const emits = defineEmits(['toggle-complete', 'delete-task']);

  const toggleComplete = () => {
    emits('toggle-complete', props.task.id);
  };

  const deleteTask = () => {
    emits('delete-task', props.task.id);
  };
</script>

<style scoped>
li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px 0;
}

.completed span {
  text-decoration: line-through;
}

button {
  background-color: red;
  color: white;
  border: none;
  padding: 5px;
  cursor: pointer;
}
</style>
