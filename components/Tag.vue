<template>
    <div :class="[
        'inline-flex items-center border border-gray-800 font-medium rounded shadow-sm transition-shadow duration-200',
        sizeClasses,
        hoverEffect,
    ]">
        <span v-if="icon" class="mr-1 text-lg">
            <i :class="icon"></i>
        </span>
        <slot>{{ text }}</slot>
    </div>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
    text: {
        type: String,
        required: false,
        default: "",
    },
    icon: {
        type: String,
        required: false,
    },
    size: {
        type: String,
        default: "md",
        validator: (value) => ["sm", "md", "lg"].includes(value),
    },
});

const sizeClasses = computed(() => {
    switch (props.size) {
        case "sm":
            return "text-sm px-2 py-1";
        case "lg":
            return "text-lg px-4 py-2";
        default:
            return "text-md px-3 py-1.5";
    }
});

const hoverEffect = "hover:shadow-md";
</script>