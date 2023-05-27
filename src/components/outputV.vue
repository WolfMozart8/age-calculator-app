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
    grid-row: 2 / 3;
    border-top: 1px solid var(--light-grey);
    margin-top: 35px;
    padding-top: 10px;

}
</style>