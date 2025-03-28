<template>
    <div v-if="movie" class="text-white pt-16 px-4 md:px-8 w-full md:w-[53%] max-w-[900px] z-50">
        <!-- Movie Title -->
        <div class="text-3xl md:text-[55px] font-semibold font-serif">
            {{ movie.name }}
        </div>

        <!-- Metadata -->
        <div class="flex flex-wrap items-center text-base md:text-lg pt-4">
            <div class="pr-4">{{ movie.year }}</div>

            <!-- Genre Tags -->
            <div v-if="movie.genre.one" class="relative pr-4">
                <span class="absolute left-[-6px] -top-[18px] text-2xl">.</span>
                <span class="pl-3">{{ movie.genre.one }}</span>
            </div>

            <div v-if="movie.genre.two" class="relative pr-4">
                <span class="absolute left-[-6px] -top-[18px] text-2xl">.</span>
                <span class="pl-3">{{ movie.genre.two }}</span>
            </div>

            <div v-if="movie.genre.three" class="relative pr-4">
                <span class="absolute left-[-6px] -top-[18px] text-2xl">.</span>
                <span class="pl-3">{{ movie.genre.three }}</span>
            </div>
        </div>

        <!-- Description -->
        <div class="text-base md:text-2xl pt-6 leading-relaxed">
            {{ movie.description }}
        </div>
    </div>
</template>

<script setup>
defineProps({ movie: Object });
</script>