<template>
    <form>
        <inputV />
        <inputV />
        <inputV />
    </form>
</template>

<script setup>
import inputV from './form/inputV.vue';
</script>

<style scoped>
form {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-row: 1 / 2;

    border-bottom: 1px solid black;
}
</style>