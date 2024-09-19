<template>
  <div id="app">
    <h1>Vue 3 Composition API To-Do List</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  components: {
    TodoList
  }
};
</script>

<style scoped>
#app {
  text-align: center;
}
</style>
