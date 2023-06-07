<script setup>
import { ref } from 'vue';
import FormV from './components/FormV.vue';
import outputV from './components/outputV.vue';

const validDate = ref(null); // last result (if valid)


</script>

<template>
  <main class="wrapper">
    <FormV @get-valid-date="(dateResult) => {validDate = dateResult;}"/>
    <outputV :result="validDate"/>
  </main>
</template>

<style>
:root {
  /* primary colors */
  --purple:hsl(259, 100%, 65%);
  --light-red: hsl(0, 100%, 67%);
  /* neutral colors */
  --white: hsl(0, 0%, 100%);
  --off-white:hsl(0, 0%, 94%);
  --light-grey: hsl(0, 0%, 86%);
  --smokey-grey: hsl(0, 1%, 44%);
  --off-black: hsl(0, 0%, 8%);

  /* font (400i - 700 - 800i)*/
  --main-font: 'Poppins', sans-serif;

}
body {
  background-color: var(--off-white);
  font-family: var(--main-font);
  font-size: 16px;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.wrapper {
  width: 40rem;
  height: 30rem;
  background-color: var(--white);
  margin: 0 auto;
  padding: 50px;

  border-radius: 20px 20px 30% 20px;

  display: grid;
  grid-template-rows: 1fr 2fr;
}
@media (max-width: 768px) {
  .wrapper {
    width: 70%;
  }
}
</style>
