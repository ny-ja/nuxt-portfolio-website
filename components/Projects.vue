<template>
    <div class="project-container">
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-2 gap-6">
            <div v-for="(project, index) in projects" :key="index"
                class="project-card border border-gray-800 bg-transparent rounded-lg overflow-hidden shadow-lg hover:scale-105 transition-transform"
                @click="openModal(project)">
                <div class="relative">
                    <video :src="project.video" class="w-full h-48 object-cover" autoplay muted loop></video>
                    <div class="absolute bottom-0 w-full p-4 bg-gradient-to-t from-black to-transparent">
                        <h3 class="text-lg text-white font-semibold">{{ project.title }}</h3>
                    </div>
                </div>
                <div class="tags flex flex-wrap gap-2 p-4">
                    <Tag v-for="(tag, i) in project.tags" :key="i" :text="tag" size="sm" color="dark" />
                </div>
            </div>
        </div>

        <div @click="selectedProject = false" v-if="selectedProject"
            class="fixed inset-0 bg-black bg-opacity-75 flex items-center justify-center z-40">
            <div
                class="modal-content bg-white dark:bg-black border border-gray-800 p-6 rounded-lg max-w-md w-full relative">
                <button class="absolute top-4 right-4 text-xl" @click="closeModal">
                    &times;
                </button>
                <h2 class="text-xl font-bold mb-4">{{ selectedProject.title }}</h2>
                <p class="mb-4 text-md">{{ selectedProject.description }}</p>
                <div class="tags flex flex-wrap gap-2">
                    <Tag v-for="(tag, i) in selectedProject.tags" :key="i" :text="tag" size="sm" color="dark" />
                </div>
                <div class="links mt-4 flex justify-between">
                    <a v-if="selectedProject.githubLink" :href="selectedProject.githubLink" target="_blank"
                        class="text-teal-400 hover:underline">
                        View Source
                    </a>
                    <a v-if="selectedProject.websiteLink" :href="selectedProject.websiteLink" target="_blank"
                        class="text-teal-400 hover:underline">
                        Visit Website
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";
import PrimsDemo from '~/assets/videos/prims-demo.mp4';
import BpwDemo from '~/assets/videos/bpw-demo.mp4';

const projects = ref([
    {
        title: "PRIMS",
        description: "A web application designed to streamline and manage resident information within a purok efficiently.",
        tags: ["Laravel", "Vue.js", "Tailwind CSS", "MySQL", "Inertia.js"],
        video: PrimsDemo,
        githubLink: "https://github.com/ny-ja/prims",
        websiteLink: "#",
    },
    {
        title: "Barangay Poblacion Website",
        description: "An online hub for Barangay Poblacion, offering residents quick access to news, events, announcements, and essential public services.",
        tags: ["Laravel", "Vue.js", "Tailwind CSS", "MySQL", "Inertia.js"],
        video: BpwDemo,
        githubLink: "https://github.com/ny-ja/barangay-poblacion",
        websiteLink: "#",
    },
]);

const selectedProject = ref(null);

const openModal = (project) => {
    selectedProject.value = project;
};

const closeModal = () => {
    selectedProject.value = null;
};
</script>

<style scoped></style>