<script setup>

import { inject } from 'vue';

const { dayData } = defineProps({
    dayData: Object,
});

const city = inject("city")

</script>

<template>
    <div class="top">
        <div class="day">{{ new Date(dayData.date).toLocaleDateString("ru-RU", { weekday: "long" }) }}</div>
        <div class="date">{{ new Date(dayData.date).toLocaleDateString("ru-RU", { day: "numeric", month: "long", year: "numeric" }) }}</div>
        <div class="city"><img src="../icons/location.svg" alt="">{{ city }}</div>
    </div>
    <div class="bottom">
        <div>
            <img :src="dayData.day.condition.icon" alt="">
        </div>
        <div class="temp">{{ dayData.day.avgtemp_c }} °C</div>
        <div class="text">{{ dayData.day.condition.text }}</div>
    </div>
</template>

<style scoped>
.top {
    display: flex;
    flex-direction: column;
    gap: 16px;
}
.day {
    font-weight: 700;
    font-size: 37px;
    text-transform: capitalize;
}
.date {
    font-weight: 500;
    font-size: 22px;
}
.city {
    display: flex;
    align-items: center;
    gap: 8px;
}
.bottom {
    display: flex;
    flex-direction: column;
    gap: 16px;
}
.temp {
    font-weight: 700;
    font-size: 50px;
}
.text {
    font-weight: 700;
    font-size: 30px;
}
</style>