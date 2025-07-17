<template>
  <header class="bg-white">
    <nav class="mx-auto flex max-w-7xl items-center justify-between p-6 lg:px-8" aria-label="Global">
      <div class="flex lg:flex-1">
        <a href="#" class="-m-1.5 p-1.5">
          <span class="sr-only">Your Company</span>
           <p class="font-roboto font-semibold ">{{logo}}</p>
        </a>
      </div>
      <div class="flex lg:hidden">
        <button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = true">
          <span class="sr-only">Open main menu</span>
          <Bars3Icon class="size-6" aria-hidden="true" />
        </button>
      </div>
      <PopoverGroup class="hidden lg:flex lg:gap-x-12 ">
        <a href="#" class="text-sm/6 font-roboto font-light text-gray-900 hover-underline-animation">Projects</a>
        <a href="#" class="text-sm/6 font-roboto font-light text-gray-900 hover-underline-animation">About</a>
        <a href="#" class="text-sm/6 font-roboto font-light text-gray-900 hover-underline-animation">Blogs</a>
      </PopoverGroup>
      <div class="hidden lg:flex lg:flex-1 lg:justify-end">
    <!-- Optional: Add a CTA button here -->
      </div>
    </nav>
    <Dialog class="lg:hidden" @close="mobileMenuOpen = false" :open="mobileMenuOpen">
      <div class="fixed inset-0 z-50" />
      <DialogPanel class="fixed inset-y-0 right-0 z-50 w-full overflow-y-auto bg-white p-6 sm:max-w-sm sm:ring-1 sm:ring-gray-900/10">
        <div class="flex items-center justify-between">
          <a href="#" class="-m-1.5 p-1.5">
            <span class="sr-only">Your Company</span>
            <p class="md:hidden font-roboto font-semibold">{{logo}}</p>
            <p class="invisible md:visible">Menu</p>
          </a>
          <button type="button" class="-m-2.5 rounded-md p-2.5 -mt-9 md:-mt-2 text-gray-700" @click="mobileMenuOpen = false">
            <span class="sr-only">Close menu</span>
            <XMarkIcon class="size-6" aria-hidden="true" />
          </button>
        </div>
        <div class="flow-root text-center md:text-start md:mt-6">
          <div class="-my-6 divide-y divide-gray-500/10">
            <div class="space-y-2 py-6">
              <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base/7 font-roboto font-light text-gray-900 hover:bg-gray-50">Projects</a>
              <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base/7 font-roboto font-light text-gray-900 hover:bg-gray-50">Blogs</a>
              <a href="#" class="-mx-3 block rounded-lg px-3 py-2 text-base/7 font-roboto font-light text-gray-900 hover:bg-gray-50">About</a>
            </div>
          </div>
        </div>
      </DialogPanel>
    </Dialog>
  </header>
</template>

<script setup>
import { ref } from 'vue'
import {
  Dialog,
  DialogPanel,
  Disclosure,
  DisclosureButton,
  DisclosurePanel,
  Popover,
  PopoverButton,
  PopoverGroup,
  PopoverPanel,
} from '@headlessui/vue'
import {
  ArrowPathIcon,
  Bars3Icon,
  ChartPieIcon,
  CursorArrowRaysIcon,
  FingerPrintIcon,
  SquaresPlusIcon,
  XMarkIcon,
} from '@heroicons/vue/24/outline'
import { ChevronDownIcon, PhoneIcon, PlayCircleIcon } from '@heroicons/vue/20/solid'

const logo = "</grshaff>"
const mobileMenuOpen = ref(false)
</script>

<style scoped>
  .read-the-docs {
    color: #888;
  }

  /* Underline text animation */
  .hover-underline-animation {
  display: inline-block;
  position: relative;
}

  .hover-underline-animation::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 1.5px;
  background-color: black; /* Default for light mode */
  transform: scaleX(0);

  transition: transform 0.3s ease-in-out;
}

  .dark .hover-underline-animation::after {
  background-color: white;
  }

  .hover-underline-animation:hover::after {
  transform: scaleX(1);
  }
</style>
