<script setup>
import { ref } from "vue";
import PrimsDemo from '~/assets/videos/prims-demo.mp4';
import BpwDemo from '~/assets/videos/bpw-demo.mp4';
import GithubIcon from '~/components/icons/GithubIcon.vue';
import GlobeIcon from '~/components/icons/GlobeIcon.vue';

const projects = ref([
    {
        title: "PRIMS",
        description: "A web application designed to streamline and manage resident information within a purok efficiently.",
        tags: ["Laravel", "Vue.js", "Tailwind CSS", "MySQL", "Inertia.js"],
        video: PrimsDemo,
        githubLink: "https://github.com/ny-ja/prims",
        websiteLink: "",
    },
    {
        title: "Barangay Poblacion Website",
        description: "An online hub for Barangay Poblacion, offering residents quick access to news, events, announcements, and essential public services.",
        tags: ["Laravel", "Vue.js", "Tailwind CSS", "MySQL", "Inertia.js"],
        video: BpwDemo,
        githubLink: "https://github.com/ny-ja/barangay-poblacion",
        websiteLink: "",
    },
]);
</script>

<template>
    <div class="project-container">
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-2 gap-6">
            <div v-for="(project, index) in projects" :key="index"
                class="project-card border border-gray-800 bg-transparent rounded-lg overflow-hidden shadow-lg">
                <div class="relative">
                    <video :src="project.video" class="w-full h-48 object-cover" autoplay muted loop></video>
                    <div class="absolute bottom-0 w-full p-4 bg-gradient-to-t from-black to-transparent">
                        <h3 class="text-lg text-white font-semibold">{{ project.title }}</h3>
                    </div>
                </div>
                <div class="details p-4">
                    <p class="mb-2 text-md">{{ project.description }}</p>
                </div>
                <div class="tags flex flex-wrap gap-2 px-4">
                    <Tag v-for="(tag, i) in project.tags" :key="i" :text="tag" size="sm" color="dark" />
                </div>
                <div class="links flex gap-1 p-4">
                    <a v-if="project.githubLink" :href="project.githubLink" target="_blank">
                        <Tag class="bg-teal-500" text="View Source" size="sm" color="dark" :icon="GithubIcon" />
                    </a>
                    <a v-if="project.websiteLink" :href="project.websiteLink" target="_blank">
                        <Tag class="bg-teal-500" text="Visit Website" size="sm" color="dark" :icon="GlobeIcon" />
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>
