<template>
    <div class="filter flex justify-center mb-4">
        <input v-model="name" placeholder="Имя" class="px-4 py-2 border rounded mr-2" />
        <select v-model="status" class="px-4 py-2 border rounded mr-2">
            <option value="">Все</option>
            <option value="Alive">Жив</option>
            <option value="Dead">Сдох</option>
            <option value="unknown">Не понятно</option>
        </select>
        <button @click="applyFilter" class="px-4 py-2 bg-blue-500 text-white rounded">Искать</button>
    </div>
</template>

<script>
import { ref } from 'vue';

export default {
    emits: ['apply-filter'],
    setup(_, { emit }) {
        const name = ref('');
        const status = ref('');

        const applyFilter = () => {
            emit('apply-filter', { name: name.value, status: status.value });
        };

        return {
            name,
            status,
            applyFilter
        };
    }
};
</script>
