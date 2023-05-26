<template>
    <div class="output">
        <output_text />
        <output_text />
        <output_text />
    </div>
</template>

<script setup>
import output_text from './output/output_text.vue';
</script>

<style scoped>
.output {
    display: flex;
    flex-direction: column;
}
</style>