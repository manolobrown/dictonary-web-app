<template>
  <div class="flex justify-between">
    <div>
      <h1 class="text-3xl font-bold mb-2 sm:text-[64px] sm:leading-[1.4]">
        {{ definition.word }}
      </h1>
      <div class="text-[#a445ed] sm:text-2xl">{{ definition.phonetic }}</div>
    </div>
    <button
      v-if="phonetic.audio"
      class="max-w-[48px] sm:max-w-[75px]"
      @click="playAudio()"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="75"
        height="75"
        viewBox="0 0 75 75"
        class="w-full group"
      >
        <g class="fill-[#A445ED]" fill-rule="evenodd">
          <circle
            cx="37.5"
            cy="37.5"
            r="37.5"
            class="opacity-25 group-hover:opacity-100"
          />
          <path d="M29 27v21l21-10.5z" class="group-hover:fill-white" />
        </g>
      </svg>
    </button>
  </div>
</template>

<script setup>
import { ref, reactive, watch, watchEffect, computed } from "vue";
const props = defineProps({ definition: Object });
const phonetic = ref("");
watchEffect(() => {
  phonetic.value = props.definition.phonetics.find((el) => el.audio !== "");
});

function playAudio() {
  const audio = new Audio(phonetic.value.audio);
  audio.play();
}
</script>
