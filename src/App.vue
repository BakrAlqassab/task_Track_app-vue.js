<template>
  <div class="container">
    <Header title="Task Tracker" />
    <AddTask @add-task="addTask" />
    <Tasks
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";
export default {
  name: "App",
  components: { Header, Tasks, AddTask },
  data() {
    return {
      tasks: [],
    };
  },

  methods: {
    deleteTask(id) {
      if (confirm("Are you sure ?")) {
        console.log("id", id);
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      console.log("toggle", id);
      this.tasks = this.tasks.map((task) => {
        return task.id === id ? { ...task, reminder: !task.reminder } : task;
      });
    },
    addTask(task) {
      console.log(task);
      this.tasks = [...this.tasks,task]
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March 1rd at 2.30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Meeting at school",
        day: "March 3rd at 1.30pm",
        reminder: true,
      },
      {
        id: 3,
        text: "Food Shopping",
        day: "March 3rd at 11.00pm",
        reminder: false,
      },
    ];
  },
};
</script>

<style  src='./css/crash.css'>
</style>
