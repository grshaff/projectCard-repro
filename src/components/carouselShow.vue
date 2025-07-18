<template>
    <div class="relative w-full" data-carousel="slide">
      <!-- Carousel wrapper -->
      <div class="relative h-56 overflow-hidden rounded-lg md:h-96">
        <!-- Carousel Items -->
        <div
          v-for="(image, index) in images"
          :key="index"
          :class="[
            'duration-700 ease-in-out absolute inset-0 transition-opacity',
            currentSlide === index ? 'opacity-100' : 'opacity-0'
          ]"
        >
          <img
            :src="image.src"
            :alt="image.alt"
            class="absolute block w-full h-full object-cover -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2"
            @error="handleImageError"
          >
        </div>
      </div>
  
      <!-- Slider indicators -->
      <div class="absolute z-30 flex -translate-x-1/2 bottom-5 left-1/2 space-x-3 rtl:space-x-reverse">
        <button
          v-for="(image, index) in images"
          :key="`indicator-${index}`"
          type="button"
          :class="[
            'w-3 h-3 rounded-full transition-colors',
            currentSlide === index 
              ? 'bg-white dark:bg-gray-800' 
              : 'bg-white/50 dark:bg-gray-800/50 hover:bg-white dark:hover:bg-gray-800'
          ]"
          :aria-current="currentSlide === index"
          :aria-label="`Slide ${index + 1}`"
          @click="goToSlide(index)"
        />
      </div>
  
      <!-- Slider controls -->
      <button
        type="button"
        class="absolute top-0 start-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none"
        @click="prevSlide"
      >
        <span class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none">
          <ChevronLeftIcon class="w-4 h-4 text-white dark:text-gray-800" />
          <span class="sr-only">Previous</span>
        </span>
      </button>
      
      <button
        type="button"
        class="absolute top-0 end-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none"
        @click="nextSlide"
      >
        <span class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none">
          <ChevronRightIcon class="w-4 h-4 text-white dark:text-gray-800" />
          <span class="sr-only">Next</span>
        </span>
      </button>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue'
  import { ChevronLeftIcon, ChevronRightIcon } from 'lucide-vue-next'
  import imagetps from '../assets/projects-img/btps/1.webp'

  // Props
  const props = defineProps({
    images: {
      type: Array,
      default: () => [
        { src: imagetps, alt: 'Project Image 1' },

      ]
    },
    autoPlay: {
      type: Boolean,
      default: true
    },
    interval: {
      type: Number,
      default: 3000
    }
  })
  
  // Reactive data
  const currentSlide = ref(0)
  let autoPlayInterval = null
  
  // Methods
  const nextSlide = () => {
    currentSlide.value = (currentSlide.value + 1) % props.images.length
  }
  
  const prevSlide = () => {
    currentSlide.value = currentSlide.value === 0 
      ? props.images.length - 1 
      : currentSlide.value - 1
  }
  
  const goToSlide = (index) => {
    currentSlide.value = index
  }
  
  const handleImageError = (event) => {
    console.error('Failed to load image:', event.target.src)
    // You can set a fallback image here if needed
    // event.target.src = '/path/to/fallback-image.jpg'
  }
  
  const startAutoPlay = () => {
    if (props.autoPlay && props.images.length > 1) {
      autoPlayInterval = setInterval(nextSlide, props.interval)
    }
  }
  
  const stopAutoPlay = () => {
    if (autoPlayInterval) {
      clearInterval(autoPlayInterval)
      autoPlayInterval = null
    }
  }
  
  // Lifecycle hooks
  onMounted(() => {
    startAutoPlay()
  })
  
  onUnmounted(() => {
    stopAutoPlay()
  })
  
  // Pause auto-play on hover
  const pauseAutoPlay = () => stopAutoPlay()
  const resumeAutoPlay = () => startAutoPlay()
  </script>