<template>
  <header
    class="flex justify-between py-6 font-bold sm:text-lg sm:pt-[58px] sm:pb-[50px]"
  >
    <div>
      <div>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="34"
          height="38"
          viewBox="0 0 34 38"
        >
          <g
            fill="none"
            fill-rule="evenodd"
            stroke="#838383"
            stroke-linecap="round"
            stroke-width="1.5"
          >
            <path
              d="M1 33V5a4 4 0 0 1 4-4h26.8A1.2 1.2 0 0 1 33 2.2v26.228M5 29h28M5 37h28"
            />
            <path stroke-linejoin="round" d="M5 37a4 4 0 1 1 0-8" />
            <path d="M11 9h12" />
          </g>
        </svg>
      </div>
    </div>
    <div class="flex items-center divide-x divide-[#979797] gap-4 sm:gap-6">
      <div class="relative">
        <label for="selectFont" class="sr-only">Select Font</label>
        <select
          name="selectFont"
          id="selectFont"
          class="appearance-none pr-6"
          @change="$emit('update:fontFace', $event.target.value)"
        >
          <option v-for="option in options" :value="option.value">
            {{ option.text }}
          </option>
        </select>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="14"
          height="8"
          viewBox="0 0 14 8"
          class="absolute right-0 top-1/2 translate-y-[-50%]"
        >
          <path
            fill="none"
            stroke="#A445ED"
            stroke-width="1.5"
            d="m1 1 6 6 6-6"
          />
        </svg>
      </div>

      <div class="pl-2 sm:pl-4 flex items-center">
        <label
          class="relative flex justify-between items-center p-2 text-xl cursor-pointer"
        >
          <input
            type="checkbox"
            class="absolute left-1/2 -translate-x-1/2 w-full h-full peer appearance-none rounded-md cursor-pointer"
            v-model="checked"
            @change="darkMode"
          />
          <span
            class="w-[42px] h-[22px] flex items-center flex-shrink-0 p-1 bg-[#757575] rounded-full duration-300 ease-in-out peer-checked:bg-[#A445ED] after:w-[14px] after:h-[14px] after:bg-white after:rounded-full after:shadow-md after:duration-300 peer-checked:after:translate-x-[20px] cursor-pointer"
          ></span>
        </label>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="22"
          height="22"
          viewBox="0 0 22 22"
        >
          <path
            fill="none"
            stroke="#838383"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="1.5"
            d="M1 10.449a10.544 10.544 0 0 0 19.993 4.686C11.544 15.135 6.858 10.448 6.858 1A10.545 10.545 0 0 0 1 10.449Z"
          />
        </svg>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";
defineProps(["fontFace"]);
defineEmits(["update:fontFace"]);

const options = ref([
  { text: "Sans Serif", value: "font-sans" },
  { text: "Serif", value: "font-serif" },
  { text: "Mono", value: "font-mono" },
]);

const checked = ref(false);

function darkMode() {
  if (checked.value) {
    document.documentElement.classList.add("dark");
  } else {
    document.documentElement.classList.remove("dark");
  }
}
</script>
