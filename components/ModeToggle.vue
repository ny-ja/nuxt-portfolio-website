<script setup>
import { ref, onMounted, computed } from 'vue';
import { useState } from '#app'; // For Nuxt's useState
import { useHead } from '@vueuse/head';
import SunIcon from '~/components/icons/SunIcon.vue';
import MoonIcon from '~/components/icons/MoonIcon.vue';

// Function to manage theme logic
function useTheme() {
  const theme = useState('theme', () => null); // Reactive theme state
  const isReady = ref(false); // Track if theme is initialized

  const currentTheme = computed(() => theme.value === 'dark');

  function applyTheme() {
    if (theme.value === 'dark' || 
        (!theme.value && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
      document.documentElement.setAttribute('data-theme', 'dark');
    } else {
      document.documentElement.removeAttribute('data-theme');
    }
  }

  function toggleTheme() {
    theme.value = theme.value === 'dark' ? 'light' : 'dark';
    localStorage.setItem('theme', theme.value);
    applyTheme();
  }

  onMounted(() => {
    const storedTheme = localStorage.getItem('theme');
    theme.value = storedTheme || (window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
    applyTheme();
    isReady.value = true;
  });

  return { currentTheme, toggleTheme, isReady };
}

// Initialize theme logic
const { currentTheme, toggleTheme, isReady } = useTheme();

// Use Nuxt's `useHead` to set initial theme state
useHead({
  script: [
    {
      children: `if (localStorage.theme === "dark" || (!('theme' in localStorage) && window.matchMedia("(prefers-color-scheme: dark)").matches)) {
        document.documentElement.setAttribute("data-theme", "dark");
      } else {
        document.documentElement.removeAttribute("data-theme");
      }`,
    },
  ],
});
</script>

<template>
  <a v-if="isReady" @click="toggleTheme" class="flex justify-center items-center">
    <SunIcon v-if="currentTheme" />
    <MoonIcon v-else />
  </a>
</template>
