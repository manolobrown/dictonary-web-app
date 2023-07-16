<script setup>
import { ref } from "vue";
import Header from "./components/Header.vue";
import Search from "./components/Search.vue";
const selected = ref("font-sans");
</script>

<template>
  <div class="container mx-auto px-4 max-w-[780px] sm:px-10" :class="selected">
    <Header v-model:font-face="selected" />
    <Search />
  </div>
</template>
