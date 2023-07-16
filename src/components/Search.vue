<template>
  <form
    id="search"
    class="flex items-center justify-between bg-[#f4f4f4] dark:bg-[#1f1f1f] border border-transparent py-[14px] px-6 rounded-2xl mb-6 sm:mb-10"
    @submit.prevent="getDefinition"
  >
    <input
      class="bg-transparent w-full placeholder:text-[#2d2d2d] placeholder:opacity-25 font-semibold sm:text-xl dark:placeholder:text-white"
      name="query"
      v-model="searchQuery"
      placeholder="Search for any word..."
    />
    <button type="submit">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="18"
        height="18"
        viewBox="0 0 18 18"
      >
        <path
          fill="none"
          stroke="#A445ED"
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="1.5"
          d="m12.663 12.663 3.887 3.887M1 7.664a6.665 6.665 0 1 0 13.33 0 6.665 6.665 0 0 0-13.33 0Z"
        />
      </svg>
    </button>
  </form>
  <SearchResult v-if="definition" :definition="definition" />
</template>

<script setup>
import { ref, watchEffect } from "vue";
import SearchResult from "./SearchResult.vue";
const API_URL = `https://api.dictionaryapi.dev/api/v2/entries/en/`;
const searchQuery = ref("");
const definition = ref("");

async function getDefinition() {
  const url = `${API_URL}${searchQuery.value}`;
  definition.value = await (await fetch(url)).json();
}
</script>
