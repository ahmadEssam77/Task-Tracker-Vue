<template>
  <div class="container">
    <Header @toggle-add-task="showTheForm" title="Task Tracker" :changeBtnTxt="showTask" />
    <AddTask @add-task="createTask" :showTask="showTask" v-if="showTask" /> <!-- v-if == v-show -->
    <Tasks
      @reminder-toggle="deleteRem"
      @delete-task="deletefun"
      :tasks="tasks"
    />
    <router-view></router-view>
    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
    Footer
  },
  data() {
    // variables
    return {
      tasks: [],
      showTask: false,
    };
  },
  methods: {
    deletefun(id) {
      if (confirm("Are you sure for deleting the task?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    deleteRem(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    createTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    showTheForm() {
      this.showTask = !this.showTask;
    }
  },
  created() {
    // life cycle vue hook  (Anything in App.vue is a global scope)
    this.tasks = [
      {
        id: 1,
        text: "Study Vue",
        date: "21-12-2021",
        time: "11:38",
        reminder: true,
      },
      {
        id: 2,
        text: "Projects with Vue",
        date: "21-01-2022",
        time: "16:15",
        reminder: true,
      },
      {
        id: 3,
        text: "Study C++",
        date: "21-02-2022",
        time: "07:10",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.container {
  padding: 15px;
  border: 1px solid #333;
  border-radius: 5px;
  max-width: 600px;
  margin: auto;
  min-height: 300px;
}

.btn {
  background-color: rgb(22, 22, 22);
  color: #fff;
  border: 1px solid green;
  padding: 7px 14px;
  border-radius: 5px;
  cursor: pointer;
}

.mRed {
  background-color: red;
}
</style>
