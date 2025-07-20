<script setup>
import { ref, computed, watchEffect, onMounted, onUnmounted  } from 'vue'
import Home from './page/main.vue'

</script>

<template>
  <div class="flex flex-col min-h-screen">
    <main class="flex-grow">
      <Home/>
    </main>
  </div>
</template>
