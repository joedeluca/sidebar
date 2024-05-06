<template>
  <div
    class="sticky z-50 opacity-50 top-0 bg-blue-500 p-0 h-19 px-4 py-2 justify-center items-center flex space-x-4 transform ease-in-out duration-300"
    :class="sideBarIsOpen ? 'ml-sidebar' : 'left-0'"
  >
    <div class="bg-pink-800">
      <button
        class="ml-1 flex items-center justify-center h-10 w-10 rounded-full focus:outline-none focus:ring-2 focus:ring-inset focus:ring-base-content"
        type="button"
        @click="$emit('openMenu', true), (sideBarIsOpen = !sideBarIsOpen)"
      >
        <span class="sr-only">Open sidebar</span>
      </button>
    </div>
    <div class="bg-pink-200 w-full">
      <input type="search" class="w-full h-full text-xl p-3" />
    </div>
    <div class="bg-yellow-700">right</div>
  </div>
</template>
<script lang="ts" setup>
import { ref } from "vue";

defineEmits({ openMenu: Boolean });
const sideBarIsOpen = ref(true);
</script>
