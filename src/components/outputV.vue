<template>
    <div class="output">
        <output_text title="years" :output-number="checkValidity(result) ? result.year : '--'"/>
        <output_text title="months" :output-number="checkValidity(result) ? result.month : '--'"/>
        <output_text title="days" :output-number="checkValidity(result) ? result.day : '--'"/>
    </div>
</template>

<script setup>
import output_text from './output/output_text.vue';
defineProps(["result"]);

const checkValidity = (item) => {
    if (item === null) {
        return false
    }
    if (item && item.day == NaN) {
        return false
    }
    else if (item) {
        return true
    }
    else {return false}
};

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