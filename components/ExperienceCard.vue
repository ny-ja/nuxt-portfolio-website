<script setup>
import { ref } from 'vue';

const props = defineProps({
    title: String,
    companyName: String,
    companyLink: String,
    duration: String,
    responsibilities: Array,
    tags: Array,
    logo: String,
});

const isCollapsed = ref(true);

const toggleCollapse = () => {
    isCollapsed.value = !isCollapsed.value;
};
</script>

<template>
    <div class="rounded-lg shadow-lg p-5 border border-gray-800 bg-transparent">
        <div class="flex items-center gap-4">
            <img :src="logo" alt="Company Logo" class="h-12 w-12 rounded-full" />
            <div>
                <h2 class="text-xl font-semibold">{{ title }}</h2>
                <a :href="companyLink" class="text-sm underline text-teal-500 hover:text-teal-700" target="_blank">{{
                    companyName }}</a>
                <p class="text-sm text-gray-500">{{ duration }}</p>
            </div>
        </div>
        <div class="mt-4">
            <button @click="toggleCollapse" class="flex items-center gap-2 text-teal-500 hover:text-teal-700">
                <span>{{ isCollapsed ? 'Show Details' : 'Hide Details' }}</span>
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor"
                    class="h-4 w-4">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        :d="isCollapsed ? 'M19 9l-7 7-7-7' : 'M9 5l7 7-7 7'" />
                </svg>
            </button>
            <transition name="fade">
                <div v-show="!isCollapsed" class="mt-4 space-y-2 text-sm leading-relaxed">
                    <p v-for="(responsibility, index) in responsibilities" :key="index">
                        {{ responsibility }}
                    </p>
                    <div class="flex gap-2 flex-wrap">
                        <Tag v-for="(tag, i) in tags" :key="i" :text="tag" size="sm" color="dark" />
                    </div>
                </div>
            </transition>
        </div>
    </div>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.fade-enter-from {
    opacity: 0;
    transform: translateY(-10px);
}

.fade-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}
</style>