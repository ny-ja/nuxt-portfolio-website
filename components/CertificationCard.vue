<template>
    <div
        class="max-w-md bg-white dark:bg-black border border-gray-800 rounded-lg shadow-md overflow-hidden">
        <div class="image-container relative h-48 bg-cover bg-center"
            :style="{ backgroundImage: `url('${backgroundImage}')` }">
            <div class="icon-container text-white bg-gray-800 opacity-60 px-5 py-5 rounded-full">
                <ChevronIcon />
            </div>
            <div class="absolute inset-0 bg-gradient-to-b from-transparent to-black opacity-50"></div>
        </div>
        <div class="p-6">
            <h2 class="text-xl font-semibold">{{ awardTitle }}</h2>
            <p class="text-sm text-gray-500 mt-1">Date: {{ date }}</p>
            <p class="text-sm text-gray-500 mt-1">Issued by: {{ issuingOrganization }}</p>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    awardTitle: {
        type: String,
        required: true
    },
    date: {
        type: String,
        required: true
    },
    issuingOrganization: {
        type: String,
        required: true
    },
    backgroundImage: {
        type: String,
        required: true
    }
});
</script>

<style scoped>
.image-container {
    background-position: top;
    background-size: cover;
    transition: background-position 1s ease-in-out;
    position: relative;
}

.image-container:hover {
    background-position: center bottom;
}

.icon-container {
    transition: transform 1s ease-in-out, opacity 1s ease-in-out;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
}

.image-container:hover .icon-container {
    transform: translate(-50%, calc(-50% + 50px));
    opacity: 0;
}
</style>