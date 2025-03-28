<template>
    <div v-if="movie" class="text-white pt-10 w-fit z-0 ">
        <!-- Movie Title -->
        <div class="text-xl md:text-3xl font-semibold font-serif">
            {{ movie.name }}
        </div>

        <!-- Metadata -->
        <div class="flex flex-wrap items-center text-base md:text-lg pt-4">
            <div class="">{{ movie.year }}</div>
            <div v-if="movie.genre.one" class="relative ">
                <span class="ml-2.5 -top-0.5 text-lg">|</span>
                <span class="pl-3">{{ movie.genre.one }}</span>
            </div>
            <div v-if="movie.genre.two" class="relative ">
                <span class="ml-2.5 -top-0.5 text-lg">|</span>
                <span class="pl-3">{{ movie.genre.two }}</span>
            </div>
            <div v-if="movie.genre.three" class="relative ">
                <span class="ml-2.5 -top-0.5 text-lg">|</span>
                <span class="pl-3">{{ movie.genre.three }}</span>
            </div>
        </div>

        <!-- Description -->
        <div class="text-base md:text-2xl pt-6 leading-relaxed">
            {{ movie.description }}
        </div>

        <!-- Preview Button -->
        <button @click="showFullVideo = true"
            class="hover110 mt-4 bg-blue-600/80 hover:bg-blue-500 text-white font-medium text-sm px-6 py-1.5 rounded-full shadow-md transition duration-300 ease-in-out">
            Preview &raquo;
        </button>
    </div>
</template>

<script setup>
import { useMovieStore } from '@/stores/movie'
import { storeToRefs } from 'pinia'

const movieStore = useMovieStore()
const { movie, showFullVideo } = storeToRefs(movieStore)
</script>