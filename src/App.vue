<template>
  <div>
    <TheNavBar @open-menu="sideBarIsOpen = !sideBarIsOpen" />
    <TheSideBar
      @open-menu="sideBarIsOpen = !sideBarIsOpen"
      :isMobile="isMobile()"
      v-model="sideBarIsOpen"
    />
    <main
      class="p-4 transform ease-in-out duration-300"
      :class="sideBarIsOpen ? 'ml-sidebar' : 'ml-0'"
    >
      <BaseCard /><BaseCard /><BaseCard /><BaseCard /><BaseCard />
    </main>
  </div>
</template>
<script setup>
import { ref } from "vue";
import TheNavBar from "./components/TheNavBar.vue";
import TheSideBar from "./components/TheSideBar.vue";
import BaseCard from "./components/BaseCard.vue";
import { useMobileDetection } from "vue3-mobile-detection";

const { isMobile } = useMobileDetection();
const sideBarIsOpen = ref(!isMobile());
</script>
