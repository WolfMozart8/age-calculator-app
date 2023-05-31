<template>
    <div class="input-v">
        <label for="date">date</label>
        <input type="text" id="date"
            :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value)">
    </div>
</template>

<script setup>
defineProps(['modelValue'])
defineEmits(['update:modelValue']);
</script>

<style scoped>
.date {
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