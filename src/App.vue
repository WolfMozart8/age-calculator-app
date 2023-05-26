<script setup>
</script>

<template>
  <main class="wrapper">
    
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
}
body {
  background-color: var(--off-white);
  font-size: 32px;
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

  border-radius: 20px 20px 30% 20px;
}
</style>
