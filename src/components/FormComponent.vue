<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulario para criação de uma nova tarefa">
        <input 
        type="text"
        class="input"
        placeholder="Qual tarefa você deseja iniciar?"
        v-model="description" />
      </div>
      <div class="column">
        <ElectronicTaskTimer @aoTemporizadorFinalizado="stopTask"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ElectronicTaskTimer from './ElectronicTaskTimer.vue';

export default defineComponent({
  name: 'FormComponent',
  emits:['aoSalvarTarefa'],
  data() {
    return {
      description: ''
    }
  },
  components: {
    ElectronicTaskTimer
  },
  methods: {
    stopTask(timeInSeconds: number) : void {
      this.$emit('aoSalvarTarefa', {
        durationInSeconds: timeInSeconds,
        description: this.description
      })
      this.description = '';
    }
  }
});
</script>
