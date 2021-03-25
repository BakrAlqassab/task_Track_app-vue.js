<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label for="">Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label for="">Day & Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>
    <div class="form-control">
      <input type="submit" value="Save Task" class="btn btb-block" />
    </div>
  </form>
</template>




<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
      if (!this.text) {
        alert(" Please add a task");
        return;
      } else if (!this.day) {
        alert(" Please add a date");
        return;
      }

      const newTask = {
        id: Math.floor(Math.random() * 100),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };
      this.$emit('add-task',newTask);
      (this.text = ""), (this.day = ""), (this.reminder = false);
    },
  },
};
</script>


<style scoped src='../css/AddTask.css'>
</style>
