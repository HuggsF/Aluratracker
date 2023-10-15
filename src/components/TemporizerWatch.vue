<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <stop-watch :timeInSeconds="timeInSeconds" />
    <button class="button" @click="startTask" :disabled="isRunning">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="stopTask" :disabled="!isRunning">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">

import { defineComponent } from "vue";
import StopWatch from "./StopWatch.vue";


export default defineComponent({
  name: "TemporizerWatch",
  emits:['onStopTask'],
  components: {
    StopWatch,
  },
  data() {
    return {
      timeInSeconds: 0,
      stopwatch: 0,
      isRunning: false
    };
  },
  methods: {
    startTask () {
        this.isRunning = true;
        this.stopwatch = setInterval(() => {
        this.timeInSeconds++;
      }, 1000);
    },
    stopTask () {
        this.isRunning = false;
        clearInterval(this.stopwatch);
        this.$emit('onStopTask', this.timeInSeconds);
        this.timeInSeconds = 0;
    },
  },
});
</script>
