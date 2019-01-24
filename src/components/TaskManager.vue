<template>
  <div class="row">
    <app-task
      v-for="(task, index) in tasks"
      @click.native="deleteTask(index)"
      @remove="$emit('delete-task', index)"
      :task="tasks[index]"></app-task>
  </div>
</template>

<script>
import Task from './Task.vue'

export default {
  props:['tasks'],
  components:{
    appTask: Task
  },
  data() {
    return {
      isActive:true
    }
  },
  methods: {
      deleteTask(index) {
        if(!this.isActive){
          this.$emit('deleteTaskEvent', index);
        }
      },
      changeToDeleteable(event){
        this.isActive = event;
      }
  }
}
</script>

<style>

</style>
