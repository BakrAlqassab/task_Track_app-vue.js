<template>
  <div class="container">
    <Header title="Task Tracker" />
    <Tasks @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
export default {
  name: "App",
  components: { Header, Tasks },
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
