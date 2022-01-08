<!-- Template -->
<template>
  <div title="double click to set/remove the reminder" @dblclick="onToggle(myTask.id)" :class="[myTask.reminder ? 'reminder' : '', 'task']">
    <h3>
      {{ myTask.text }}
      <i @click="onDelete(myTask.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ myTask.date }}</p>
    <p>{{ myTask.time }}</p>
  </div>
</template>

<!-- Script -->
<script>
export default {
  name: "Task",
  props: {
    myTask: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-task", id);
    },
    onToggle(id) {
      this.$emit('reminder-toggle', id);
    }
  },
};
</script>

<!-- Style -->
<style scoped>
div {
  background-color: #ccc;
  padding: 7px;
  margin-bottom: 5px;
  border-radius: 3px;
}

h3 {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-right: 10px;
}

i {
  cursor: pointer;
  color: red;
}

.reminder {
  border-left: 5px solid green;
}

.task {
  background-color: #ddd;
}
</style>
