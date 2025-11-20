<script setup>
const data = defineModel({
    type: String,
    required: true
})
</script>

<template>
    <input type="text" v-model="data">
</template>

<style scoped>
input {
    background-color: var(--bg-card-day);
    font-size: 18px;
    color: var(--white);
    padding: 15px 20px;
    border: 0;
    border-radius: 10px;
    height: 58px;
    outline: none;
    box-shadow: 1px 2px 4px 0px #222831;
}
input::placeholder {
    color: var(--color-placeholder);
}
</style>