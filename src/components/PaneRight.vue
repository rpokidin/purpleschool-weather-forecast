<script setup>
import Error from "./Error.vue";
import DayCard from "./DayCard.vue";
import CitySelect from "./CitySelect.vue";
import Stat from "./Stat.vue";
import { computed } from "vue";

const { error, data, activeIndex } = defineProps({
    error: Object,
    data: Object,
    activeIndex: Number,
});

const emit = defineEmits(["select-index", "select-city"]);

const statData = computed(() => {
    return [
        {
            label: "Влажность",
            stat: data.forecast.forecastday[activeIndex].day.avghumidity + " %"
        },
        {
            label: "Осадки",
            stat: data.forecast.forecastday[activeIndex].day.totalprecip_mm + " мм"
        },
        {
            label: "Ветер",
            stat: data.forecast.forecastday[activeIndex].day.maxwind_kph + " км/ч"
        }
    ]
})

</script>

<template>
    <Error v-if="error" :error="error?.error?.message" />
    <template v-if="data">
        <div class="day-stat">
            <Stat v-for="item in statData" v-bind="item" :key="item.label" />
        </div>
        <div class="day-card-list">
            <DayCard 
            v-for="(item, index) in data.forecast.forecastday" v-bind="item" :key="item.date"
            :icon="item.day.condition.icon"
            :date="new Date(item.date)" 
            :temp="item.day.avgtemp_c"
            :is-active="activeIndex == index"
            @click="() => emit('select-index', index)"
            />
        </div>
    </template>
    <CitySelect />
</template>

<style scoped>
.day-stat {
  display: flex;
  flex-direction: column;
  gap: 16px;
  margin-bottom: 60px;
}
.day-card-list {
  display: flex;
  gap: 1px;
  margin-bottom: 60px;
}
</style>