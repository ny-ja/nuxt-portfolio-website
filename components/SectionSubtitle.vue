<template>
    <div class="section-subtitle group relative">
        <p class="text-lg sm:text-xl font-medium text-gray-600 group-hover:text-gray-800 transition duration-300">
            <slot name="subtitle" />
        </p>
        <div 
            class="underline mt-1 w-8 h-0.5 bg-gradient-to-r from-teal-400 to-blue-500 group-hover:w-12 transition-all duration-300">
        </div>
    </div>
</template>

<style scoped>
.section-subtitle {
    margin-top: 1rem;
    text-align: center;
}

.underline {
    margin: 0 auto;
    border-radius: 9999px;
}
</style>
