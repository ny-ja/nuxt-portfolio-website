<template>
    <button @click="toggleTheme" class="p-2 rounded bg-gray-200 dark:bg-gray-800">
      <span v-if="isDarkMode" class="text-yellow-400">☀️ Light Mode</span>
      <span v-else class="text-blue-600">🌙 Dark Mode</span>
    </button>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const isDarkMode = ref(false)
  
  const toggleTheme = () => {
    isDarkMode.value = !isDarkMode.value
    const theme = isDarkMode.value ? 'dark' : 'light'
    document.documentElement.setAttribute('data-theme', theme)
    localStorage.setItem('theme', theme)
  }
  
  // Apply theme on load
  useHead({
    script: [
      {
        children: `
          if (localStorage.theme === "dark" || (!('theme' in localStorage) && window.matchMedia("(prefers-color-scheme: dark)").matches)) {
            document.documentElement.setAttribute("data-theme", "dark")
          } else {
            document.documentElement.removeAttribute("data-theme")
          }
        `,
      },
    ],
  })
  
  // Set initial state based on data-theme
  isDarkMode.value =
    document.documentElement.getAttribute('data-theme') === 'dark'
  </script>
  