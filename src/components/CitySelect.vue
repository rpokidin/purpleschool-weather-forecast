<script setup>
import { inject, ref } from 'vue';
import Button from './Button.vue';
import Input from './Input.vue';

const city = inject("city")
const inputValue = ref(city.value)

let isEdited = ref(false)

const select = () => {
    isEdited.value = false
    city.value = inputValue.value
}

const edit = () => {
    isEdited.value = true
}

const vFocus = {
    mounted: (el) => el.focus()
}

</script>

<template>
    <div class="city-select" v-if="isEdited">
        <Input 
            placeholder="Введите город" 
            v-model="inputValue" 
            @keyup.enter="select()"
            v-focus
        />
        <Button @click="select()">Сохранить</Button>
    </div>
    <Button v-else @click="edit()">
    <img src="../icons/location.svg" alt="">Изменить город
    </Button>
</template>

<style scoped>
.city-select {
    display: flex;
    align-items: center;
    gap: 12px;
}
</style>