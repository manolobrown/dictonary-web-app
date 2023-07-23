<template>
  <div>
    <div class="relative flex py-5 items-center sm:py-8">
      <h2 class="flex-shrink mr-4 text-lg font-bold sm:text-2xl">
        <em>noun</em>
      </h2>
      <div class="flex-grow border-t border-[#e9e9e9]"></div>
    </div>

    <h3 class="text-[#757575] mb-4 sm:text-xl">Meaning</h3>
    <ul
      role="list"
      class="marker:text-[#8f19e8] list-disc pl-3 space-y-3 mb-6 sm:text-lg sm:pl-8 sm:mb-8"
    >
      <li class="pl-3" v-for="item in definition.meanings[0].definitions">
        {{ item.definition }}
      </li>
    </ul>
    <div class="flex gap-6 text-[#757575] sm:text-xl">
      Synonyms
      <div class="font-bold text-[#a445ed]">
        <span v-for="item in props.definition.meanings[0].synonyms.join(', ')">
          {{ item }}
        </span>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({ definition: Object });
</script>
