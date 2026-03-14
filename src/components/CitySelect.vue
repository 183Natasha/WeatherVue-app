<script setup>
import { ref } from 'vue';
import AppButton from './Button/AppButton.vue';
import IconLocation from './icons/IconLocation.vue';
import AppInput from './AppInput.vue';

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
    <div class="city-select">
        <div v-show="isEdited" class="city-input">
            <AppInput placeholder="Введите город"></AppInput>
            <AppButton @click="select()">
                Сохранить.
            </AppButton>
        </div>

        <AppButton v-show="!isEdited" @click="edit">
            <IconLocation></IconLocation>
            Изменить город
        </AppButton>
    </div>




</template>

<style scoped>
.city-input {
    display: flex;
    gap: 12px;

}

.city-select {
    width: 420px;
}
</style>