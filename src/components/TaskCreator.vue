<template>
  <div class="creator-box">
    <p> Hello i'm the task creator.</p>
    <div class="box-divider">
      <div class="column-55">
        <label> Task message </label>
        <b-input v-model="msg"></b-input>
      </div>
      <div class="column-15">
        <label> Task time </label>
        <b-input v-model="time" type="number"></b-input>
      </div>
      <div class="column-15">
        <label> Format time </label>
        <b-select placeholder="Select a time" v-model="selected">
          <option v-for="(format, index) in formats" :key="index" :value="format">
            {{ format.name }}
          </option>
        </b-select>
      </div>
      <div class="column-rest">
        <button @click.prevent="createTask" class="button is-info">Create new Task</button>
      </div>
    </div>
</div>
</template>

<script>
import uuidv4 from "uuid/v4";

export default {
  data: function() {
    return {
      msg: "",
      time: 0,
      selected: {},
      formats: [
        {
          name: "miliseconds",
          multiplier: 1
        },
        {
          name: "seconds",
          multiplier: 1000
        },
        {
          name: "minutes",
          multiplier: 60000
        }
      ]
    };
  },

  methods: {
    createTask() {
      this.$emit("addTask", {
        id: uuidv4(),
        name: this.msg,
        time: this.time,
        multiplier: this.selected.multiplier
      });
    }
  }
};
</script>

<style>
.box-divider {
  display: flex;
  width: 100%;
}
.column-15 {
  width: 15%;
  margin: 10px;
}
.column-55 {
  width: 55%;
  margin: 10px;
}
.column-rest {
  width: auto;
  margin: 10px;
  align-self: flex-end;
}
.creator-box {
  background: #f6f6f6;
  padding: 10px;
  margin: 10px;
}
</style>
