<script setup>
import { ref, computed, watchEffect } from 'vue'
import navBar from './components/navBar.vue'
import FooterD from './components/footer.vue'
import Home from './page/main.vue'
import About from './page/about.vue'
import Blogs from './page/blogs.vue'
// import NotFound from './page/NotFound.vue' // Optional

const routes = {
  '/': { component: Home, title: 'Home | Grshaff Portfolio' },
  '/about': { component: About, title: 'About | Grshaff Portfolio' },
  '/blogs': { component: Blogs, title: 'Blogs | Grshaff Portfolio' },
}

const currentPath = ref(window.location.hash || '#/')
window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash || '#/'
})

const currentRoute = computed(() => {
  return routes[currentPath.value.slice(1)] || {
    component: { template: '<div class="p-4 text-red-500">Page Not Found</div>' },
    title: '404 | Grshaff Portfolio'
  }
})

// 🔥 Dynamically update page title
watchEffect(() => {
  document.title = currentRoute.value.title
})

</script>

<template>
  <div class="flex flex-col min-h-screen">
    <navBar :current-path="currentPath" />
    <main class="flex-grow">
      <component :is="currentRoute.component" />
    </main>
    <FooterD />
  </div>
</template>
