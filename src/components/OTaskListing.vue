<template>
  <ul>
    <o-task
      v-for="(task, index) in Tasks"
      :task="task"
      :delete-button="deleteButton"
      :key="index"
      >{{ task }}</o-task
    >
  </ul>
</template>
<script>
import OTask from "./OTask.vue";
export default {
  components: {
    OTask,
  },
  data() {
    return {
      Tasks: ["task1", "task2", "task3"],
    };
  },
  methods: {
    deleteButton(index) {
      this.Tasks.splice(index, 1);
    },
  },
};
</script>

<style></style>
