<template>
    <div class="btn-container">
        <button
            @click="$emit('create-output')"
        ><img src="../../assets/img/icon-arrow.svg" alt="button"></button>
    </div>
</template>

<script setup>
defineEmits(["create-output"])
</script>

<style scoped>
.btn-container {
    display: flex;
    justify-content: center;
    align-items: center;

    position: absolute;
    right: 0px;
    top: 105px;
}
button {
    padding: 25px;
    border-radius: 50%;
    border: none;
    background-color: var(--purple);
}
</style>