<script setup>
import { createReturnStatement } from "@vue/compiler-core";
import { ref, computed, onMounted } from "vue";

const query = ref("");
const my_anime = ref([]);
const search_results = ref([]);

const my_anime_asc = computed(() => {
  return my_anime.value.sort((a, b) => {
    createReturnStatement.title.localCompate(b.title);
  });
});

const searchAnime = () => {
  const url = `https://api.jikan.moe/v4/anime?q=${query.value}`;
  fetch(url)
    .then((res) => res.json())
    .then((data) => {
      search_results.value = data.data;
    });
};
</script>

<template>
  <main>Hello, World!</main>
</template>

<style></style>
