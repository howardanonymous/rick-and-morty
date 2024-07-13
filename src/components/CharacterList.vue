<!-- src/components/CharacterList.vue -->
<template>
  <div>
    <input v-model="search" placeholder="Search characters..." />
    <div class="character-list">
      <CharacterCard
        v-for="character in filteredCharacters"
        :key="character.id"
        :character="character"
      />
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue';
import CharacterCard from './CharacterCard.vue';

export default {
  components: { CharacterCard },
  setup() {
    const search = ref('');
    const characters = ref([]);
    
    const fetchCharacters = async () => {
      const response = await fetch('https://rickandmortyapi.com/api/character');
      const data = await response.json();
      characters.value = data.results;
    };

    const filteredCharacters = computed(() => {
      return characters.value.filter(character =>
        character.name.toLowerCase().includes(search.value.toLowerCase())
      );
    });

    fetchCharacters();

    return { search, filteredCharacters };
  },
};
</script>

<style scoped>
.character-list {
  display: flex;
  flex-wrap: wrap;
}
</style>
