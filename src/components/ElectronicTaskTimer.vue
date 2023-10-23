<template>
    <div class="is-flex is-align-items-center">
        <ProgressiveClock :timeInSeconds="timeInSeconds"></ProgressiveClock>
        <button class="button" @click="start()" :disabled="isActive">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="stop()" :disabled="!isActive">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import ProgressiveClock from './ProgressiveClock.vue';

export default defineComponent({
    name: 'ElectronicTaskTimer',
    emits:['aoTemporizadorFinalizado'],
    components: {
        ProgressiveClock
    },
    data() {
        return {
            timeInSeconds: 0,
            cronometro: 0,
            isActive: false
        }
    },
    methods: {
        start() {
            this.isActive = true
            this.cronometro = setInterval(() => {
                this.timeInSeconds += 1
            }, 1000);
        },
        stop() {
            this.isActive = false
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.timeInSeconds);
            this.timeInSeconds = 0;
        }
    }
});
</script>