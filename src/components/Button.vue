<script setup></script>

<template>
    <button class="btn">
        <slot />
    </button>
</template>

<style scoped>
.btn {
    background: var(--btn-default);
    width: 100%;
    height: 58px;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    font-weight: 600;
    font-size: 20px;
    color: var(--white);
    padding: 14px;
    border-radius: 10px;
}
.btn :deep(img) {
    margin-right: 13px;
}
.btn:hover {
    background: var(--btn-hover);
}
</style>