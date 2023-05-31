<template>
    <form @submit.prevent="">
        <inputV v-model="birth.day" />
        <inputV v-model="birth.month" />
        <inputV v-model="birth.year" />
        <buttonV @create-output="createDate(birth)" />
    </form>
</template>

<script setup>
import { ref } from 'vue';
import inputV from './form/inputV.vue';
import buttonV from './form/buttonV.vue';

const birth = ref({
    day: "",
    month: "",
    year: ""
})

const createDate = (obj) => {
    const birthdate = new Date(`${obj.year}-${obj.month}-${obj.day}`) // yyyy-mm-dd
    const today = new Date()

    let yearsOld = today.getFullYear() - birthdate.getFullYear()
    let monthsOld = today.getMonth() - birthdate.getMonth()
    let daysOld = today.getDate() - birthdate.getDate()

    if ( // check if the final yearsOld is correct
        today.getMonth() < birthdate.getMonth() ||
        (today.getMonth() === birthdate.getMonth() && today.getDate() < birthdate.getDate())) 
        {yearsOld--;}

    if ( // same as above, but by months and days
        monthsOld < 0 || (monthsOld === 0 && daysOld < 0)) {
        monthsOld = 12 - Math.abs(monthsOld);
        daysOld = birthdate.getDate() - today.getDate() + getLastDay(today.getMonth(), today.getFullYear()); 
    }

};

const getLastDay = (mm, yyyy) => { // last day of the month
    const lastDay = new Date(yyyy, mm + 1, 0)
    return lastDay.getDate()
};
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