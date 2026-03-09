<script setup>
import { ref } from 'vue';
import AppButton from './Button/AppButton.vue';
import IconLocation from './icons/IconLocation.vue';

const emit = defineEmits({
    selectCity(payload) {
        console.log(`Validating payload:${payload}`)
        return payload ? true : false
    }
})

let isEdited = ref(false)

function select() {
    isEdited.value = false
    emit('selectCity', 'London')
}

function edit() {
    isEdited.value = true
}

</script>

<template>
    {{ isEdited }}
    <AppButton @click="edit">
        Изменить город
    </AppButton>
    <input id="city" type="text" name="city">
    <AppButton @click="select()">
        <IconLocation></IconLocation>
        Сохранить
    </AppButton>


</template>

<style scoped></style>