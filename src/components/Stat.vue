<script setup>
    const { label, stat } = defineProps({
        label: String,
        stat: String
    })
</script>

<template>
    <div class="stat">
        <div class="stat-name">{{ label }}</div>
        <div class="stat-val">{{ stat }}</div>
    </div>
</template>

<style scoped>
.stat {
    display: flex;
    justify-content: space-between;
    gap: 16px;
    font-size: 28px;
}
.stat-name {
    font-weight: 700;
    text-transform: uppercase;
}
.stat-val {
    font-weight: 500;
}
</style>