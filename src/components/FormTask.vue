<template>
  <div class="box formtask">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulario para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="description"
        />
      </div>
      <div class="column">
        <TemporizerWatch @on-stop-task="finalizeTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TemporizerWatch from "./TemporizerWatch.vue";

export default defineComponent({
  name: "FormTask",
  emits: ["onSaveTask"],
  components: {
    TemporizerWatch,
  },
  data() {
    return {
      description: "",
    };
  },
  methods: {
    finalizeTask(timeInSeconds: number): void {
      this.$emit("onSaveTask", {
        lengthInSeconds: timeInSeconds,
        description: this.description,
      });
      this.description = "";
    },
  },
});
</script>

<style>
.formtask{
  color: var(--primary-text);
  background-color: var(--primary-bg);
}
</style>
