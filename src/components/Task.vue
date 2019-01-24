<template>
  <div @click="remove"
  style="margin:20px; padding:10px; border-radius: 10px;"
  v-bind:style="{ background: activeColor}">
    <div style="display:flex; width:100%;">
      <div style="width:50%; margin:auto; color:white;">
        <label> {{task.name}} </label>
      </div>
      <div style="width:50%; margin:auto;">
        <progress class="progress is-info" :value="progress" max="100"></progress>
      </div>
      <p style="margin:10px; color:white;">{{milisecondsLeft / 1000}} </p>
    </div>
  </div>
</template>

<script>
export default {
  props:['task'],
  data(){
    return {
      milisecondsLeft:0,
      isActive:true,
      activeColor: '#9bffb3',
    }
  },
  methods:{
    remove(){
      if(this.milisecondsLeft<=0){
        this.$emit('remove');
      }
    }
  },
  computed:{
    progress(){
      return (this.milisecondsLeft/(this.task.time * this.task.multiplier))*100;
    }
  },
  mounted() {
    const interval = 1000;
    this.milisecondsLeft = this.task.time * this.task.multiplier;
    const handler = setInterval( () => {
      this.milisecondsLeft-=interval;
      if (this.milisecondsLeft <= 0) {
        this.activeColor='#ff9b9b';
        clearInterval(handler);
      }
    }, interval);
  }
}
</script>

<style>

</style>
