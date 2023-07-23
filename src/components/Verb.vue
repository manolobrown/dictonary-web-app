<template>
  <div>
    <div class="relative flex py-5 items-center sm:py-8">
      <h2 class="flex-shrink mr-4 text-lg font-bold sm:text-2xl">
        <em>verb</em>
      </h2>
      <div class="flex-grow border-t border-[#e9e9e9]"></div>
    </div>

    <h3 class="text-[#757575] mb-4 sm:text-xl">Meaning</h3>
    <ul
      role="list"
      class="marker:text-[#8f19e8] list-disc pl-3 space-y-3 mb-6 sm:text-lg sm:pl-8"
    >
      <li class="pl-3" v-for="item in definition.meanings[1].definitions">
        {{ item.definition }}
        <div class="text-[#757575] mt-3">
          {{ item.example }}
        </div>
      </li>
    </ul>
    <div
      class="text-[#757575] text-sm border-t border-[#e9e9e9] pt-6 pb-8 sm:flex sm:gap-5"
    >
      <span class="underline underline-offset-2">Source</span>
      <div class="flex gap-1 sm:gap-4 items-center mt-2 sm:mt-0">
        <a
          v-for="item in definition.sourceUrls"
          class="underline underline-offset-1 decoration-1 text-[#2d2d2d] dark:text-white"
          :href="item"
          target="_blank"
          >{{ item }}</a
        >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="14"
          height="14"
          viewBox="0 0 14 14"
        >
          <path
            fill="none"
            stroke="#838383"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="1.5"
            d="M6.09 3.545H2.456A1.455 1.455 0 0 0 1 5v6.545A1.455 1.455 0 0 0 2.455 13H9a1.455 1.455 0 0 0 1.455-1.455V7.91m-5.091.727 7.272-7.272m0 0H9m3.636 0V5"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({ definition: Object });
</script>
