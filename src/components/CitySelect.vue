<script setup>
import { onBeforeMount, onMounted, onUpdated, ref } from 'vue';
import AppButton from './Button/AppButton.vue';
import IconLocation from './icons/IconLocation.vue';
import AppInput from './AppInput.vue';

onBeforeMount(() => {
    console.log('City select - before mounted')
})

onMounted(() => {
    console.log('City select mounted')
})

onUpdated(() => {
    console.log('City select - updated')
})


const emit = defineEmits({
    selectCity(payload) {
        console.log(`Validating payload:${payload}`)
        return payload ? true : false
    }
})

let isEdited = ref(false)
const city = ref('')

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
        {{ city }}
        <div v-if="isEdited" class="city-input">
            <AppInput v-model="city" placeholder="Введите город"></AppInput>
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