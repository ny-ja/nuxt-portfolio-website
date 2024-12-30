<template>
    <a href="/files/cv.pdf" download="Johnny_Ermio_CV.pdf"
        class="group relative w-36 sm:w-40 lg:w-44 h-9 sm:h-10 lg:h-11 flex items-center border border-teal-500 bg-teal-500 text-white font-medium cursor-pointer overflow-hidden transition-all duration-300 hover:bg-teal-700 active:bg-teal-800 active:border-teal-800">
        <span
            class="absolute left-4 sm:left-5 lg:left-6 text-xs sm:text-sm lg:text-base transition-transform duration-300 group-hover:text-transparent">
            <slot name="text" />
        </span>
        <span
            class="absolute right-0 w-8 sm:w-9 lg:w-10 h-full bg-teal-700 flex items-center justify-center transition-all duration-300 group-hover:w-full">
            <DownloadIcon />
        </span>
    </a>
</template>