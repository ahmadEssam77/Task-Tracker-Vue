<!-- Template -->
<template>
  <form @submit="saveTask">
    <div>
      <label for="task">Task</label>
      <input type="text" v-model="text" name="task" id="task" />
    </div>
    <div>
      <label for="theDate">Date</label>
      <input type="date" v-model="date" name="theDate" id="theDate" />
    </div>
    <div>
      <label for="theTime">Time</label>
      <input type="time" v-model="time" name="theTime" id="theTime" />
    </div>
    <div class="last">
      <label for="reminder">Set a reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" id="reminder" />
    </div>
    <button type="submit" class="btn">Save Task</button>
  </form>
</template>

<!-- Svript -->
<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      date: "",
      time: "",
      reminder: false,
    };
  },
  methods: {
    saveTask(e) {
      e.preventDefault();

      if (!this.text) {
        alert("please add a task");
        return;
      }

      const newTask = {
        id: Math.floor(Math.random() * 100),
        text: this.text,
        date: this.date,
        time: this.time,
        reminder: this.reminder
      };

      this.$emit("add-task", newTask);

      // Clear the form after add task
      this.text = "";
      this.date = "";
      this.time = "";
      this.reminder = false;
    },
  },
};
</script>

<!-- Style -->
<style scoped>
input {
  width: 95%;
  margin: 10px auto;
  display: block;
}

.last {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.last label {
  width: 100%;
}

.btn {
  width: 95%;
  display: block;
  margin: 10px auto;
}
</style>
