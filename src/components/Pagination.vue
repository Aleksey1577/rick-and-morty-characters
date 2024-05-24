<template>
    <div class="pagination flex justify-center items-center my-4">
        <button @click="previousPage" :disabled="!info.prev"
            class="px-4 py-2 bg-gray-200 rounded mr-2">Previous</button>
        <span>Page {{ currentPage }} of {{ info.pages }}</span>
        <button @click="nextPage" :disabled="!info.next" class="px-4 py-2 bg-gray-200 rounded ml-2">Next</button>
    </div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    props: {
        info: Object,
        currentPage: Number
    },
    emits: ['change-page'],
    setup(props, { emit }) {
        const previousPage = () => {
            emit('change-page', props.currentPage - 1);
        };

        const nextPage = () => {
            emit('change-page', props.currentPage + 1);
        };

        return {
            previousPage,
            nextPage
        };
    }
});
</script>
