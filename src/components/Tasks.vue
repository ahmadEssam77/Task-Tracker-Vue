<!-- Template -->
<template>
  <div :key="task.id" v-for="task in tasks">
    <Task @reminder-toggle="this.$emit('reminder-toggle', task.id)" @delete-task="this.$emit('delete-task', task.id)" :myTask="task" />
  </div>
</template>

<!-- Script -->
<script>
import Task from "./Task.vue";
// @delete-task="onDeleteMid(task.id)"

export default {
  name: "Tasks",
  props: {
    tasks: Array, // passing data from parent to a child, this is the child. The passing data coming from App component
  },
  components: {
    Task,
  },
  emits: ['delete-task', 'reminder-toggle'],
};
</script>

<!-- Style -->
<style scoped></style>
