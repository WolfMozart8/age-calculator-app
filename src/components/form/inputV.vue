<template>
    <div class="input-v">
        <label for="date">{{ title }}</label>
        <input
        type="number"
        id="date"
        :value="modelValue"
        @input="$emit('update:modelValue',$event.target.value)"
        :placeholder="placeH"
        required>
    </div>
        <!-- :value="modelValue" -->
        <!-- @input="$emit('update:modelValue', $event.target.value)"  -->
        <!-- @input="validation($event)" -->
</template>

<script setup>
import { onMounted, ref, watch } from 'vue';

defineProps(['modelValue', "title", "placeH", "minV", "maxV"])
defineEmits(['update:modelValue']);

const isValid = ref(null)
const isBlank = ref(true)
const inputValue = ref(null)

const validation = (e) => {
    inputValue.value = e.target.value
    isValid.value = e.target.checkValidity()
    isBlank.value = e.target.validity.valueMissing
};

defineExpose({
    inputValue,
    isValid,
    isBlank,
});
</script>

<style scoped>
/* remove increment arrows */
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button,
input[type="number"] {
    -webkit-appearance: none;
    /* Chrome, Safari */
    -moz-appearance: textfield;
    /* Firefox */
    appearance: none;
    margin: 0;
}

.date {
    letter-spacing: 1.2;
}

.red {
    background-color: red;
    color: yellow;
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
}
</style>
