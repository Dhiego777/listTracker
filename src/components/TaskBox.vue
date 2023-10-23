<template>
    <div class="box has-text-weught-bold">
        <slot></slot>
    </div>
</template>
<script lang="ts">
import { defineComponent} from 'vue';

export default defineComponent({
    name: 'TaskBox'
})

</script>
<style scoped>
.box {
    background: #FAF0CA;
}
</style>