<template>
    <task-box>
        <div class="columns">
            <div class="column is-7">
                {{ task.description || 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <ProgressiveClock :timeInSeconds="task.durationInSeconds"></ProgressiveClock>
            </div>
        </div>
    </task-box>
</template>
<script lang="ts">
import { defineComponent, PropType } from 'vue';
import ProgressiveClock from './ProgressiveClock.vue';
import ITask from '@/interfaces/ITask';
import TaskBox from './TaskBox.vue';

export default defineComponent({
    name:'AssignmentTask',
    components: {
        ProgressiveClock,
        TaskBox
    },
    props: {
        task: {
            type: Object as PropType<ITask>,
            required: true
        }
    }
})
</script>