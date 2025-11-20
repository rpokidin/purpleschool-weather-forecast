<script setup>
    const props = defineProps({
        error: String,
    })
</script>

<template>
    <div class="error" v-if="props.error">{{ props.error }}</div>
</template>

<style scoped>
.error {
    background-color: var(--bg-card-day);
    font-size: 18px;
    text-align: center;
    padding: 15px;
    margin-bottom: 25px;
    border-radius: 25px;
}
</style>