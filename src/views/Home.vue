<template>
  <div class="home">
    <div class="header">
      <TheHeader />
    </div>
    <div class="tasks-header">
      <h1>Task Board</h1>
      <div class="select-tasks">
        <h4>All Tasks</h4>
        <button class="material-icons">keyboard_arrow_down</button>
      </div>
    </div>
    <Tasks />
  </div>
</template>

<script>
import TheHeader from '../components/TheHeader.vue'
import Tasks from '../components/Tasks.vue'
export default {
  name: 'Home',
  components: { TheHeader, Tasks },
}
</script>

<style scoped>
.home {
  background-color: var(--dark);
}

.tasks-header {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 1rem;
  padding-bottom: 1rem;
}

.tasks-header h1 {
  margin-left: 3rem;
}

.select-tasks {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 3rem;
  background-color: var(--blue-btn);
  width: 150px;
  height: 50px;
  border-radius: 1rem;
}

.select-tasks h4 {
  margin-right: 1rem;
}
</style>
