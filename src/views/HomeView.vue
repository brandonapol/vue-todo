<template>
  <div id="app">
    <div class="center">
      <div class="interface">
        <h1>My Todo List</h1>
        <TodoList />
      </div>
    </div>
  </div>
</template>

<script>
import TodoList from '../components/TodoList.vue'

export default {
  components: {
    TodoList
  }
}
</script>