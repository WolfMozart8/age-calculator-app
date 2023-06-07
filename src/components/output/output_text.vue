<template>
    <div class="date-text">
        <p><span class="date-number">{{ outputNumber }}</span>{{ title }}</p>
    </div>
</template>

<script setup>
defineProps(["title", "outputNumber"]);
</script>

<style scoped>
.date-text {
    font-weight: 800;
    font-style: italic;
}
.date-number {
    color: var(--purple);
}
p {
    font-size: 5rem;
    margin: 0;
}
@media (max-width: 768px) {
    div {
        margin-bottom: -30px;
    }
    p {
        font-size: 4rem;
    }
}
@media (max-width: 480px) {
    div {
        margin-bottom: 0;
    }
    p {
        font-size: 3rem;
    }
}
</style>
