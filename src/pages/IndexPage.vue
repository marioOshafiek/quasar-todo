<template>
  <q-page class="flex flex-center">
    <h1>Vue002</h1>
    <br />
    <div>
      <o-task-listing></o-task-listing>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import OTaskListing from "src/components/OTaskListing.vue";

export default defineComponent({
  name: "IndexPage",
  components: {
    OTaskListing,
  },
  data() {
    return {
      tasks: ["task1", "task2", "task3"],
    };
  },
  methods: {
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
  },
});
</script>
