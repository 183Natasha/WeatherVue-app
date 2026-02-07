<script setup>
import AppButton from './Button/AppButton.vue';
import IconLocation from './icons/IconLocation.vue';

</script>

<template>
    <AppButton>
        Изменить город
    </AppButton>
    <input id="city" type="text" name="city">
    <AppButton>
        <IconLocation></IconLocation>
        Сохранить
    </AppButton>

    
</template>

<style scoped></style>