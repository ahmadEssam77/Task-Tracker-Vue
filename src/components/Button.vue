<!-- Template -->
<template>
  <button @click="showAddTask"  :style="{ backgroundColor: color }" class="btn">
    {{ text }}
  </button>
</template>

<!-- Script -->
<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String,
  },
  methods: {
    showAddTask() {
      this.$emit('toggle-add-task');
    },
  },
};
</script>

<!-- Style -->
<style scoped></style>
