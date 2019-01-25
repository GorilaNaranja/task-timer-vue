<template>
  <div class="row">
    <app-task
      v-for="(task, index) in tasks"
      :key="task.id"
      :task="tasks[index]"
      @remove="$emit('delete-task', $event)"
    />
  </div>
</template>

<script>
import Task from "./Task.vue";

export default {
  components: {
    appTask: Task
  },

  props: {
    tasks: {
      type: Array,
      required: true
    }
  },

  data() {
    return {
      isActive: true
    };
  },

  methods: {
    deleteTask(index) {
      if (!this.isActive) {
        this.$emit("deleteTaskEvent", index);
      }
    },

    changeToDeleteable(event) {
      this.isActive = event;
    }
  }
};
</script>

<style>
</style>
