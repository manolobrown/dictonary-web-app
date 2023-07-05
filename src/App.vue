<script setup>
import Header from "./components/Header.vue";
import Search from "./components/Search.vue";
import SearchResult from "./components/SearchResult.vue";
</script>

<template>
  <div class="container mx-auto px-4 max-w-[780px] sm:px-10">
    <Header />
    <Search class="mb-6" />
    <SearchResult />
  </div>
</template>
