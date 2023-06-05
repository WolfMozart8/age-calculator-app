<template>
    <form @submit.prevent="$emit('getValidDate', ageResult)">
        <inputV v-model:model-value="birth.day" title="DAY" place-h="DD" />
        <inputV v-model:model-value="birth.month" title="MONTH" place-h="MM"/>
        <inputV v-model:model-value="birth.year" title="YEAR" place-h="YYYY"/>
        <buttonV @create-output="calculateAge(birth)" />
    </form>
</template>

<script setup>
import { ref } from 'vue';
import inputV from './form/inputV.vue';
import buttonV from './form/buttonV.vue';

defineEmits(["getValidDate"]);

const birth = ref({
    day: null,
    month: null,
    year: null,
})

const ageResult = ref(null)

const isValid = (obj) => {
    const lastday = getLastDay(obj.month, obj.year)
    if (obj.day === "" || obj.day === null || obj.month === "" || obj.month === null || obj.year === "" || obj.year === null) {
        return false
    }
    else if (obj.day > lastday) {
        console.log("select a valid day");
        return false
    }
    else {
        return true
    }
}
// const val = (e) => {
//     e.target.checkValidity()
//     e.target.validity.valueMissing
// }
// // check the correct max uinputDuts
// const actualYear = ref(new Date().getFullYear())
// const lastDay = computed(() => {
//     const lastDay = new Date(birth.value.year, birth.value.month + 1, 0)
//     // const lastDay = new Date(inputY.value.inputValue, inputM.value.inputValue + 1, 0)
//     return lastDay.getDate()
// })



// const form = ref(null)
// const inputD = ref(null)
// const inputM = ref(null)
// const inputY = ref(null)

// const validation = (input1, input2, input3) => {
//     const value1 = input1.value.inputValue
//     const value2 = input2.value.inputValue
//     const value3 = input3.value.inputValue

//     const isValid1 = input1.value.isValid
//     const isValid2 = input2.value.isValid
//     const isValid3 = input3.value.isValid

//     const isBlank1 = input1.value.isBlank
//     const isBlank2 = input2.value.isBlank
//     const isBlank3 = input3.value.isBlank

//     if (isBlank1 || isBlank2 || isBlank3) {
//         return false
//     }
//     else if (!isValid1 || !isValid2 || !isValid3) {
//         return false
//     }
//     else {
//         birth.value.day = value1
//         birth.value.month = value2
//         birth.value.year = value3

//         return true
//     }

//     console.log(value1 + " " + isValid1 + " " + isBlank1)
//     console.log(value2 + " " + isValid2 + " " + isBlank2)
//     console.log(value3 + " " + isValid3 + " " + isBlank3)
// }
const calculateAge = (obj) => {
    const birthdate = new Date(`${obj.year}-${obj.month}-${obj.day}`) // yyyy-mm-dd
    // const birthdate = new Date(`${inputY.value.inputValue}-${inputM.value.inputValue}-${inputD.value.inputValue}`) // yyyy-mm-dd
    const today = new Date()

    if (!isValid(obj)) {
        return
    }

    let yearsOld = today.getFullYear() - birthdate.getFullYear()
    let monthsOld = today.getMonth() - birthdate.getMonth()
    let daysOld = today.getDate() - birthdate.getDate()

    if (daysOld > getLastDay(today.getMonth(), today.getFullYear())) {
        daysOld = getLastDay(today.getMonth(), today.getFullYear()) - Math.abs(daysOld) + 1
        monthsOld++
    }
    if (daysOld < 0) {
        monthsOld--
        daysOld = getLastDay(today.getMonth(), today.getFullYear()) - Math.abs(daysOld) + 1
    }
    if (monthsOld >= 12) {
        monthsOld = Math.abs(monthsOld) - 12
        yearsOld++
    }
    if (monthsOld < 0) {
        monthsOld = 12 - Math.abs(monthsOld)
        yearsOld--
    }

    ageResult.value = { day: daysOld, month: monthsOld, year: yearsOld }
    console.log(ageResult.value);
    console.log(birth.value);
};

const getLastDay = (mm, yyyy) => { // last day of the month
    const lastDay = new Date(yyyy, mm + 1, 0)
    return lastDay.getDate()
};

</script>

<style>
form {
    display: grid;
    position: relative;
    grid-template-columns: repeat(4, 1fr);
    grid-row: 1 / 2;

    /* border-bottom: 1px solid black; */
}
form > div input,
form > div .error {
    background-color: red;
}
@media (max-width: 768px) {
    form {
        grid-template-columns: repeat(3, 1fr);
    }
}
</style>
