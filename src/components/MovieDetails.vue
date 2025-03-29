<template>
    <div v-if="movie" class="text-white pt-5.5 md:px-10 md:pt-18 z-0">
        <!-- Movie Title -->
        <div class="text-xl md:text-3xl font-semibold font-serif fade-in-left">
            {{ movie.name }}
        </div>

        <!-- Metadata -->
        <div class="flex flex-wrap items-center text-xs md:text-sm fade-in-left mt-2.5 rounded-full">
            <div class="text-blue-300">{{ movie.year }}</div>

            <div v-if="movie.genre.one" class="relative ">
                <span class="ml-2.5 -top-0.5">|</span>
                <span class="pl-3 text-blue-300">{{ movie.genre.one }}</span>
            </div>
            <div v-if="movie.genre.two" class="relative ">
                <span class="ml-2.5 -top-0.5">|</span>
                <span class="pl-3">{{ movie.genre.two }}</span>
            </div>
            <div v-if="movie.genre.three" class="relative ">
                <span class="ml-2.5 -top-0.5">|</span>
                <span class="pl-3">{{ movie.genre.three }}</span>
            </div>
        </div>

        <!-- Description -->
        <div class="text-sm md:text-base lg:text-lg pt-4 leading-relaxed fade-in-left tracking-wider">
            {{ movie.description }}
        </div>

        <!-- Preview Button -->
        <button @click="showFullVideo = true"
            class="md:scale-110 hover110 mt-4.5 ml-1 gradient-blue-button text-white text-sm  px-5.5 py-0.5 pb-1 rounded-full fade-in-left-slow">
            <div class="flex items-center justify-center">
                <span>Preview </span>
                <span class="pl-1 pt-1"> <i class="pi pi-eye" /></span>
            </div>
        </button>
    </div>
</template>

<script setup>
import { useMovieStore } from '@/stores/movie'
import { storeToRefs } from 'pinia'

const movieStore = useMovieStore()
const { movie, showFullVideo } = storeToRefs(movieStore)
</script>