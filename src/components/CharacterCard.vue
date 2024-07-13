<!-- src/components/CharacterCard.vue -->
<template>
  <div class="character-card">
    <img :src="character.image" :alt="character.name" />
    <h3>{{ character.name }}</h3>
  </div>
</template>

<script>
export default {
  props: ['character'],
};
</script>

<style scoped>
.character-card {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  margin: 10px;
  width: 200px;
  text-align: center;
}
.character-card img {
  max-width: 100%;
  border-radius: 5px;
}
</style>
