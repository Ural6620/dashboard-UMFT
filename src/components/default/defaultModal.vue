<template>
  <TransitionRoot as="template" :show="toggle">
    <Dialog as="div" class="relative z-50" @close="close">
      <TransitionChild as="template" enter="ease-out duration-300" enter-from="opacity-0" enter-to="opacity-100"
        leave="ease-in duration-200" leave-from="opacity-100" leave-to="opacity-0">
        <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" />
      </TransitionChild>

      <div class="fixed inset-0 z-10 overflow-y-auto">
        <div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
          <TransitionChild as="template" enter="ease-out duration-300"
            enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
            enter-to="opacity-100 translate-y-0 sm:scale-100" leave="ease-in duration-200"
            leave-from="opacity-100 translate-y-0 sm:scale-100"
            leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95">
            <slot />
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
</template>
<script setup>
import { storeToRefs } from 'pinia'
import { Dialog, TransitionChild, TransitionRoot } from '@headlessui/vue'

import { useFullStore } from '@/stores/usefull/modal';
const usefull = useFullStore();
const { toggle } = storeToRefs(usefull);

const close = () => {
  usefull.setToggle(false)
}
</script>
<style lang=""></style>
