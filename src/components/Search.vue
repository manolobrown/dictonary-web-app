<template>
  <form
    action=""
    class="flex items-center justify-between bg-[#f4f4f4] dark:bg-[#1f1f1f] border border-transparent py-[14px] px-6 rounded-2xl sm:mb-10"
  >
    <input
      class="bg-transparent w-full placeholder:text-[#2d2d2d] placeholder:opacity-25 font-semibold sm:text-xl dark:placeholder:text-white"
      type="text"
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
</template>

<script setup></script>

<style lang="scss" scoped></style>
