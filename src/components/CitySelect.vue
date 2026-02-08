
<script setup>
import AppButton from './Button/AppButton.vue';
import IconLocation from './icons/IconLocation.vue';

const emit = defineEmits(['city-select'])

function select(){
    emit('city-select', 'London')
}

</script>

<template>
    <AppButton @click="select()">
        Изменить город
    </AppButton>
    <input id="city" type="text" name="city">
    <AppButton >
        <IconLocation></IconLocation>
        Сохранить
    </AppButton>


</template>

<style scoped></style>