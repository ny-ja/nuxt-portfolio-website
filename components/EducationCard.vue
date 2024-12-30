<script setup>
const props = defineProps({
    degree: String,
    schoolName: String,
    schoolLink: String,
    duration: String,
    logo: String,
});
</script>

<template>
    <div class="rounded-lg shadow-lg p-5 border border-gray-800 bg-transparent">
        <div class="flex items-center gap-4">
            <img :src="logo" alt="School Logo" class="h-12 w-12 rounded-full" />
            <div>

                <a :href="schoolLink" class="text-xl font-semibold underline text-teal-500 hover:text-teal-700"
                    target="_blank">{{
                        schoolName }}</a><br />
                <span class="text-sm ">{{ degree }}</span>
                <p class="text-sm text-gray-500">{{ duration }}</p>
            </div>
        </div>
    </div>
</template>