<template>
    <form>
        <inputV />
        <inputV />
        <inputV />
        <buttonV />
    </form>
</template>

<script setup>
import inputV from './form/inputV.vue';
import buttonV from './form/buttonV.vue';
</script>

<style scoped>
form {
    display: grid;
    position: relative;
    grid-template-columns: repeat(4, 1fr);
    grid-row: 1 / 2;

    /* border-bottom: 1px solid black; */
}
</style>