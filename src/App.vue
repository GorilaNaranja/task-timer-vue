<template>
  <div id="app">
    <h1 style="font-size:30px; margin:20px;"> Welcome to Task Timer App</h1>
    <app-global-header :tasks="tasks"></app-global-header>
    <app-task-creator @addTask="newTask"></app-task-creator>
    <app-task-manager :tasks="tasks" @delete-task="deleteTask"></app-task-manager>
  </div>
</template>

<script>
import GlobalHeader from "./components/GlobalHeader.vue";
import TaskCreator from "./components/TaskCreator.vue";
import TaskManager from "./components/TaskManager.vue";

export default {
  name: "app",

  components: {
    appGlobalHeader: GlobalHeader,
    appTaskCreator: TaskCreator,
    appTaskManager: TaskManager
  },

  data: function() {
    return {
      tasks: []
    };
  },

  methods: {
    newTask(task) {
      this.tasks.push(task);
    },

    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px;
}
</style>
