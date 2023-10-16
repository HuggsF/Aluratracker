<template>
  <DescriptionBoxVue>
    <div class="columns">
      <div class="column is-7">{{ task.description || 'Task without description.'  }} </div>
      <div class="column">
        <StopWatch :time-in-seconds="task.lengthInSeconds"/>
      </div>
    </div>
  </DescriptionBoxVue>
</template>

<script lang="ts">

import { defineComponent, PropType } from "vue";
import StopWatch from "./StopWatch.vue";
import ITaskUnit from "../interfaces/ITaskUnit";
import DescriptionBoxVue from "./DescriptionBox.vue";

export default defineComponent({
  name: "TaskUnit",
  components: {
    StopWatch,
    DescriptionBoxVue,
  },
  props: {
    task: {
      type: Object as PropType<ITaskUnit>,
      required: true,
    },
  }
});
</script>

<style scoped>
.box {
  align-items: center;
  padding: 1rem;
  margin-bottom: 1rem;
  box-shadow: #737eaf 0px 0px 5px 0px;
  border-radius: 5px;
  background-color: azure;
}
</style>
