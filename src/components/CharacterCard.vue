<template>
    <div class="flex flex-col items-center shadow-md rounded-lg p-4 m-4 text-center">
        <img :src="character.image" :alt="character.name" class="w-[100px] h-[100px] rounded-[90px]" />
        <h2 class="text-xl font-bold mt-4">{{ character.name }}</h2>
        <p>Статус: {{ character.status }}</p>
        <p>Вид: {{ character.species }}</p>
        <p>Пол: {{ character.gender }}</p>
        <p>Происхождение: {{ character.origin.name }}</p>
        <p>Локация: {{ character.location.name }}</p>
    </div>
</template>

<script>
export default {
    props: {
        character: Object
    }
};
</script>

