<template>
  <div @dblclick="$emit('toggle-reminder',task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>
      {{ task.text }}
      <!--           Font Awesome             -->
      <i @click="onDelete(task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>
<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      console.log(id);
      this.$emit("delete-task", id);
    },
  },
};
</script>
<style scoped src='../css/Task.css'>
</style>
