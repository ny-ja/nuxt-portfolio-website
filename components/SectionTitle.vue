<template>
    <div class="section-title group relative">
        <div
            class="icon-container absolute -left-10 top-1/2 transform -translate-y-1/2 hidden sm:flex items-center justify-center w-12 h-12 rounded-full bg-gradient-to-r from-teal-400 to-blue-500 shadow-lg group-hover:scale-110 transition duration-300">
            <div class="w-6 h-6 text-white">
                <slot name="icon" />
            </div>
        </div>
        <h2 class="lg:text-3xl text-2xl font-bold group-hover:text-teal-500 transition duration-300">
            <slot name="title" />
        </h2>
        <div
            class="divider mt-2 w-16 h-1 bg-gradient-to-r from-teal-400 to-blue-500 group-hover:w-24 transition-all duration-300">
        </div>
    </div>
</template>

<style scoped>
.section-title {
    padding-left: 3rem;
}

.icon-container {
    transition: all 0.3s ease;
}

.divider {
    border-radius: 9999px;
}
</style>