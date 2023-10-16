<template>
  <main class="columns is gapless is-multiline sideBarColumn" :class="{ 'dark-mode' : darkModeActivated }">
    <div class="column is-one-quarter" :class="aaa">
      <SideBar @onToggleDarkMode="changeTheme" />
    </div>
    <div class="column is three-quarter content">
      <FormTask @onSaveTask="addTask" />
      <div class="list">
        <TaskUnit v-for="(task, index) in tasks" :key="index" :task="task" />
        <DescriptionBox v-if="isTaskListEmpty"> GO GET A TASK! >:D </DescriptionBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">

import { defineComponent } from 'vue';

import SideBar from './components/SideBar.vue';
import FormTask from './components/FormTask.vue';
import TaskUnit from './components/TaskUnit.vue';
import ITaskUnit from './interfaces/ITaskUnit';
import DescriptionBox from './components/DescriptionBox.vue';

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    FormTask,
    TaskUnit,
    DescriptionBox,
  },
  data () {
    return {
      tasks: [] as ITaskUnit[],
      darkModeActivated: false,
    }
  },
  computed:{
    isTaskListEmpty(): boolean {
      return this.tasks.length === 0;
    },
    aaa(): string{
      return 'aaa'
    }
  },
  methods: {
    addTask (task: ITaskUnit) : void {
      this.tasks.push(task);
    },
    changeTheme(darkModeActivated: boolean) {
      this.darkModeActivated = darkModeActivated;
    }
}});
</script>

<style>
.list {
  padding: 1.25rem;
}
main {
  --primary-bg: #fff;
  --primary-text: #000;

}
main.dark-mode {
  --primary-bg: #2b2d42;
  --primary-text: #ddd;

}
.content {
  background-color: var(--primary-bg);
}
.aaa{
  padding: 0%;
}
</style>
