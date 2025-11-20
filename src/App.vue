<script setup>
import { onMounted, provide, ref, watch } from 'vue';
import PaneRight from './components/PaneRight.vue';
import PaneLeft from './components/PaneLeft.vue';

const data = ref()
const error = ref()
const activeIndex = ref(0)
const city = ref("Москва")

provide("city", city)

watch(city, () => {
  getCity(city.value)
})

onMounted(() => {
  getCity(city.value)
})

const API_ENDPOINT = "http://api.weatherapi.com/v1"

async function getCity(city) {
  const params = new URLSearchParams({
    q: city,
    lang: "ru",
    key: "acb068a02ced42e6be3110501252210",
    days: 3
  })
  const res = await fetch(`${API_ENDPOINT}/forecast.json?${params.toString()}`)

  if (res.status != 200) {
    error.value = await res.json()
    data.value = null
    return
  }

  error.value = null
  data.value = await res.json()

}
</script>

<template>
  <main class="main">
    <div class="left">
      <PaneLeft
        v-if="data"
        :day-data="data.forecast.forecastday[activeIndex]"
      />
    </div>
    <div class="right">
      <PaneRight 
        :data
        :error
        :active-index="activeIndex"
        @select-index="(index) => (activeIndex = index)"
      />
    </div>
  </main>
</template>

<style scoped>
.main {
  display: flex;
  align-items: center;
}
.left {
  background: url(/public/bg-left.png) no-repeat;
  background-size: cover;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 500px;
  height: 660px;
  padding: 55px 35px;
  border-radius: 30px;
}
.right {
  background-color: var(--bg-card);
  width: 525px;
  padding: 55px;
  border-radius: 0 25px 25px 0;
}
</style>