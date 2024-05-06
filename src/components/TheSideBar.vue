<template>
  <TransitionRoot :show="isOpen" as="template">
    <TransitionChild
      as="template"
      enter="ease-in-out duration-300 transform"
      enter-from="-translate-x-full"
      enter-to="translate-x-0"
      leave="ease-in-out duration-300 transform"
      leave-from="translate-x-0"
      leave-to="-translate-x-full"
    >
      <div
        class="sidebar"
        :class="[isMobile ? 'sidebar-mobile' : 'sidebar-desktop']"
      >
        <div class="p-0 h-19 bg-green-500 flex justify-center items-center">
          nav
        </div>
        menu
        <button
          v-if="isMobile"
          @click="$emit('openMenu', true), (sideBarIsOpen = !sideBarIsOpen)"
        >
          close
        </button>
      </div>
    </TransitionChild>
  </TransitionRoot>
</template>
<script lang="ts" setup>
import { ref } from "vue";
import {
  Disclosure,
  DisclosureButton,
  DisclosurePanel,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { useVModel } from "@vueuse/core";

const props = defineProps({
  modelValue: {
    type: Boolean,
    default: true,
  },
  isMobile: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits({ openMenu: Boolean }, "update:modelValue");

const isOpen = useVModel(props, "modelValue", emit);

const openOnFirstLoad = ref(props.isMobile);
</script>
