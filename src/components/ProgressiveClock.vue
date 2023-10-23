<template>
  <section class="pr-3">
    <strong>{{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ProgressiveClock',
  props: {
    timeInSeconds: {
      type:Number,
      default: 0
    }
  },
  computed: {
    tempoDecorrido(): string {
      return new Date(this.timeInSeconds * 1000).toISOString().substring(11, 19)
    }
  },
})

</script>