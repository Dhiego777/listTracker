<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <side-bar></side-bar>
    </div>
    <div class="column is-three-quarter">
      <form-component @aoSalvarTarefa="saveTask"></form-component>
      <div class="list">
        <task-box v-if="isEmptyList">
          Você não adicionou nenhuma tarefa
        </task-box>
        <assignment-task v-for="(task, index) in tasks" :key="index" :task="task"></assignment-task>
      </div>
    </div>
  </main>
  
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue';
import FormComponent from './components/FormComponent.vue';
import AssignmentTask from './components/AssignmentTask.vue';
import ITask from './interfaces/ITask'
import TaskBox from './components/TaskBox.vue';

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    FormComponent,
    AssignmentTask,
    TaskBox
  },
  data() {
    return {
      tasks: [] as ITask[]
    }
  },
  computed: {
    isEmptyList(): boolean {
      return this.tasks.length === 0
    }
  },
  methods: {
    saveTask(task: ITask) {
      this.tasks.push(task)
    }
  }
});
</script>

<style>
  .list{
    padding: 1.25rem;
  }
</style>
