<template>

    <div class="input-v">
        <label :class="classes" for="date">{{ title }}</label>
        <input
        ref="input"
        :class="classes"
        type="number"
        id="date"
        :value="modelValue"
        @input="$emit('update:modelValue',$event.target.value)"
        :placeholder="placeH"
        required>
        <span :title="elementTitle" v-if="input" :class="classes">{{ !error ? "" : (input.value ? errorMessage : "This field is required") }}</span>
    </div>

</template>

<script setup>
import { onMounted, ref } from 'vue';

const input = ref(null)

defineProps(['modelValue', "title", "placeH", "minV", "maxV", "classes", "error", "errorMessage", "elementTitle"])
defineEmits(['update:modelValue']);

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
span {
    display: none;
}

label {
    font-size: 1rem;
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
input.error {
    border-color: var(--light-red);
}
label.error {
    color: var(--light-red);
}
span.error {
    display: inline;
    font-family: var(--main-font);
    font-size: 0.7rem;
    font-style: italic;
    font-weight: 400;
    color: var(--light-red);
}
</style>
