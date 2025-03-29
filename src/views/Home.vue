<script setup>
import SideNav from "@/components/SideNav.vue";
import MovieDetails from "@/components/MovieDetails.vue";
import VideoCarousel from "../components/VideoCarousel.vue";
import TopNav from "@/components/TopNav.vue";
import Footer from "@/components/Footer.vue";

import { ref, onMounted, computed } from "vue"
import movies from "../data/movies.json";
import { useMovieStore } from "../stores/movie";
import { storeToRefs } from "pinia";

const useMovie = useMovieStore();
const { movie, showFullVideo } = storeToRefs(useMovie);

onMounted(() => {
    console.log("Movies JSON:", movies[0][0]); // Check what you're assigning
    setTimeout(() => {
        movie.value = movies[0][0];
        console.log("Current movie:", movie.value);
    }, 100);
});

const filteredMovies = computed(() => {
    const index = categories.indexOf(selectedCategory.value)
    return index !== -1 ? movies[index] : []
})

const categories = ["Popular", "Horror", "Featured"]
const selectedCategory = ref("Popular")


</script>

<template>
    <div class="w-full min-h-screen bg-black flex flex-col">
        <TopNav />
        <!-- Sidebar -->
        <SideNav />

        <!-- Main content (when not in full screen) -->
        <div v-if="!showFullVideo">

            <!-- Top Section: Movie preview video -->
            <div class="relative w-full h-[50vh] xl:h-[55vh] bg-black overflow-hidden">

                <div class="absolute z-10 h-full w-full bg-gradient-to-r from-black/80 via-black/15 to-black/0" />
                <div class="absolute z-10 h-full w-full bg-gradient-to-l from-black/5 via-black/0 to-black/0" />
                <div class="absolute z-10 h-full w-full bg-gradient-to-t from-black via-black/0 to-black/0" />
                <div class="absolute z-10 h-full w-full bg-gradient-to-b from-black via-black/0 to-black/0" />


                <MovieDetails v-if="movie" :movie="movie" class="absolute z-50 left-12 px-4 w-[70%] fade-in-left" />


                <video v-if="movie" :src="'/videos/' + movie.name + '.mp4'" autoplay loop muted playsinline
                    class="absolute z-0 top-0 right-0 h-full w-full object-cover fade-in" />
            </div>

            <!-- Category Filter Buttons -->
            <div class="w-full flex flex-wrap gap-1.5 px-6 md:px-16 pt-2 pb-1 fade-in-left">
                <button v-for="cat in categories" :key="cat" @click="selectedCategory = cat" :class="[
                    'px-2.5 py-1 rounded-full text-xs transition hover110',
                    selectedCategory === cat
                        ? 'gradient-blue-button text-white'
                        : 'bg-white/10 text-white/50 hover:bg-white/35 hover:text-white/70'
                ]">
                    {{ cat }}
                </button>
            </div>

            <!-- Bottom Section: Carousels -->
            <div class="relative w-full overflow-y-auto px-6.5 md:px-16.5">
                <VideoCarousel v-if="filteredMovies.length" :category="selectedCategory + ' Movies'"
                    :movies="filteredMovies" class="pb-12" />

            </div>

            <!-- Gradient overlay -->
            <!--<div class="absolute z-20 h-[50vh] w-full bottom-0 bg-gradient-to-t from-black via-black pointer-events-none" /> -->
            <Footer />
        </div>

        <!-- Full-screen video view -->
        <div v-else class="relative w-full h-screen bg-black z-[999]">
            <div @click="showFullVideo = false"
                class="absolute top-30 md:top-10 left-1/2 -translate-x-1/2 z-50 px-4 py-3.5 text-white/80 bg-black/35 rounded-full cursor-pointer hover125 hover:text-blue-400 transition">
                <i class="pi pi-arrow-circle-left" style="font-size: 1.6rem"></i>
            </div>

            <video :src="'/videos/' + movie.name + '.mp4'" autoplay loop controls
                class="absolute z-40 w-full h-screen bg-black" />
        </div>

    </div>

</template>