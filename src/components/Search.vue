<template>
  <form
    id="search"
    class="flex items-center justify-between border border-transparent mb-6 sm:mb-10 relative"
    @submit.prevent="submitForm"
    @input="hasError = false"
  >
    <input
      class="bg-[#f4f4f4] dark:bg-[#1f1f1f] py-[14px] pl-6 pr-12 w-full rounded-2xl placeholder:text-[#2d2d2d] placeholder:opacity-25 font-semibold sm:text-xl focus:outline-none focus-visible:outline-none active:outline-[#A445ED] dark:placeholder:text-white"
      :class="{ 'border-[#ff5252] border focus-visible:border-0': hasError }"
      name="query"
      v-model="searchQuery"
      placeholder="Search for any word..."
    />
    <button type="submit" class="absolute right-6">
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
    <div v-if="hasError" class="text-[#ff5252] absolute top-full mt-2">
      Whoops, can’t be empty…
    </div>
  </form>
  <SearchResult v-if="definition[0]" :definition="definition" />
  <div v-else>
    <h1 class="text-3xl font-bold mb-2 sm:text-[64px] sm:leading-[1.4]">
      {{ definition.title }}
    </h1>
    <div class="text-[#a445ed] sm:text-2xl mb-3">{{ definition.message }}</div>
    <div class="text-[#a445ed] sm:text-2xl">{{ definition.resolution }}</div>
  </div>
</template>

<script setup>
import { ref, watchEffect, computed } from "vue";
import SearchResult from "./SearchResult.vue";
const API_URL = `https://api.dictionaryapi.dev/api/v2/entries/en/`;
const searchQuery = ref("");
const definition = ref("");
const hasError = ref(false);

function submitForm() {
  if (searchQuery.value) {
    getDefinition();
    hasError.value = false;
  } else {
    hasError.value = true;
  }
}

async function getDefinition() {
  try {
    const url = `${API_URL}${searchQuery.value}`;
    definition.value = await (await fetch(url)).json();
  } catch (err) {
    console.log(err);
  }
}
</script>
