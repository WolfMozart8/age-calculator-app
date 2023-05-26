<template>
    <div class="input-v">
    <label for="day">Day</label>
    <input type="text" id="day">
    </div>
</template>

<script setup>

</script>

<style scoped>
label {
    font-size: 24px;
    margin-bottom: 15px;
    color: var(--smokey-grey);
    font-weight: 700;
}
.input-v {
    display: flex;
    flex-direction: column;
}
input {
    font-size: 32px;
    padding: 8px 16px;
    width: 60%;
}
</style>