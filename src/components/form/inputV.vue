<template>
    <div class="input-v">
        <label for="day">DAY</label>
        <input type="text" id="day">
    </div>
</template>

<script setup>

</script>

<style scoped>
.day {
    letter-spacing: 1.2;
}

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
    font-family: var(--main-font);
    font-weight: 700;
    padding: 8px 16px;
    width: 60%;
    border: 1px solid var(--light-grey);
    border-radius: 5px;
}</style>