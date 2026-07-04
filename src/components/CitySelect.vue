<script setup>
import { onMounted, onWatcherCleanup, ref, watch, watchEffect } from 'vue';
import AppButton from './Button/AppButton.vue';
import IconLocation from './icons/IconLocation.vue';
import AppInput from './AppInput.vue';



let isEdited = ref(false)
const city = ref('Moscow')

onMounted(()=>{
    emit('selectCity', city.value)
})

const emit = defineEmits({
    selectCity(payload) {
        return payload ? true : false
    }
})

function select() {
    isEdited.value = false
    emit('selectCity', city.value)
}

function edit() {
    isEdited.value = true
}

</script>

<template>
    <div class="city-select">
        <div v-if="isEdited" class="city-input">
            <AppInput v-model="city" placeholder="Введите город" @keyup.enter="select()"></AppInput>
            <AppButton @click="select()">
                Сохранить.
            </AppButton>
        </div>

        <AppButton v-if="!isEdited" @click="edit">
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