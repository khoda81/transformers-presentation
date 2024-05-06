<script setup lang="ts">
import { defineProps } from "vue";

const props = defineProps({
    tokens: {
        type: Array as () => string[],
        required: true,
    },
    initialColorIndex: {
        type: Number,
        default: 0,
    },
    colors: {
        type: Array as () => string[],
        default: () => [
            "rgba(107, 64, 216, 0.5)",
            "rgba(104, 222, 122, 0.4)",
            "rgba(244, 172, 54, 0.4)",
            "rgba(239, 65, 70, 0.4)",
            "rgba(39, 181, 234, 0.4)",
            "rgba(107, 64, 216, 0.5)",
        ],
    },
});

</script>

<template>
    <span v-for="(token, index) in props.tokens" :key="token" class="token"
        :style="{ backgroundColor: props.colors[(index + props.initialColorIndex) % props.colors.length] }">
        {{ token }}
    </span>
</template>

<style scoped>
.token {
    margin: 0.07em;
    padding: 0 0.1em;
    border-radius: 0.3em;
    line-height: 1.5em;
    white-space: pre-wrap;
}
</style>
