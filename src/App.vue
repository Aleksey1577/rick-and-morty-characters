<template>
  <div class="">
    <h1 class="mb-[50px]">Rick and Morty персонажи</h1>
    <Filter @apply-filter="applyFilter" />
    <div class="character-list">
      <CharacterCard v-for="character in characters" :key="character.id" :character="character" />
    </div>
    <Pagination :info="info" :currentPage="currentPage" @change-page="changePage" />
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import CharacterCard from './components/CharacterCard.vue';
import Pagination from './components/Pagination.vue';
import Filter from './components/Filter.vue';

export default {
  components: {
    CharacterCard,
    Pagination,
    Filter
  },
  setup() {
    const characters = ref([]);
    const info = ref({});
    const currentPage = ref(1);
    const name = ref('');
    const status = ref('');

    const fetchCharacters = async (page = 1) => {
      const response = await fetch(`https://rickandmortyapi.com/api/character?page=${page}&name=${name.value}&status=${status.value}`);
      const data = await response.json();
      characters.value = data.results;
      info.value = data.info;
    };

    const changePage = (page) => {
      currentPage.value = page;
      fetchCharacters(page);
    };

    const applyFilter = (filter) => {
      name.value = filter.name;
      status.value = filter.status;
      fetchCharacters(1);
    };

    onMounted(() => {
      fetchCharacters();
    });

    return {
      characters,
      info,
      currentPage,
      changePage,
      applyFilter
    };
  }
};
</script>

