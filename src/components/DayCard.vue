<script setup>
const { icon, date, temp, isActive } = defineProps({
    icon: String,
    date: Date,
    temp: Number,
    isActive: Boolean
})
</script>

<template>
    <button class="day-card" :class="{ active: isActive }">
        <img :src="icon" alt="">
        <div class="day-card__date">
            {{ date.toLocaleString("ru-RU", { weekday: "short" }) }}
        </div>
        <div class="day-card__temp">
            {{ temp }} °C
        </div>
    </button>
</template>

<style scoped>
.day-card {
    background-color: var(--bg-card-day);
    display: flex;
    flex-direction: column;
    align-items: center;
    flex-grow: 1;
    color: var(--white);
    gap: 15px;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 1px 2px 4px 0px #222831;
    border: 0;
}
.day-card:hover {
    background-color: var(--bg-card-day-h);
}
.day-card__date {
    font-size: 20px;
}
.day-card__temp {
    font-weight: 700;
    font-size: 20px;
}
.day-card.active {
    background-color: var(--white);
    color: var(--black);
}
</style>