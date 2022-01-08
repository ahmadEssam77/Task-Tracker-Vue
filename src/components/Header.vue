<!-- Template -->
<template>
  <header>
    <h1>{{ title }}</h1>
    <Button @toggle-add-task="$emit('toggle-add-task');" :text="!changeBtnTxt ? 'Add Task' :'Close'" :color="!changeBtnTxt? 'green' : 'maroon'" />
  </header>
</template>

<!-- Script -->
<script>
import Button from "./Button.vue";

export default {
  name: "Header",
  props: {
    title: String,
    changeBtnTxt: Boolean,
  },
  components: {
    Button,
  },
};
</script>

<!-- Style -->
<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
