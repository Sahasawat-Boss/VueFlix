<script setup>
import SideNav from "@/components/SideNav.vue";
import MovieDetails from "@/components/MovieDetails.vue";
import VideoCarousel from "../components/VideoCarousel.vue";


import { onMounted } from "vue";
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

</script>

<template>
    <div class="w-full h-screen bg-black overflow-hidden">
        <!-- Sidebar -->
        <SideNav />

        <!-- Main content (when not in full screen) -->
        <div v-if="!showFullVideo">

            <!-- Top Section: Movie preview video -->
            <div class="relative w-full h-[55vh] xl:h-[65vh] bg-black overflow-hidden">
                <div class="absolute z-10 h-full w-full bg-gradient-to-r from-black via-black/30 to-black/0" />

                <MovieDetails v-if="movie" :movie="movie"
                    class="absolute z-50 left-14 pt-18 top-0 px-4 w-[70%] fade-in-left" />


                <video v-if="movie" :src="'/videos/' + movie.name + '.mp4'" autoplay loop muted
                    class="absolute z-0 top-0 right-0 h-full w-full object-cover fade-in" />

                <div class="absolute z-10 h-full w-full bg-gradient-to-t from-black via-black/10 to-black/0" />
            </div>



            <!-- Bottom Section: Carousels -->
            <div class="relative w-full h-[60vh] overflow-y-auto px-6 md:px-16">
                <VideoCarousel class="pb-6 pt-1" category="Popular Movies" :movies="movies[0]" />
                <VideoCarousel class="pb-6" category="Horror Movies" :movies="movies[1]" />
                <VideoCarousel class="pb-32" category="Featured Movies" :movies="movies[2]" />
            </div>

            <!-- Gradient overlay -->
            <!--<div class="absolute z-20 h-[50vh] w-full bottom-0 bg-gradient-to-t from-black via-black pointer-events-none" /> -->
        </div>

        <!-- Full-screen video view -->
        <div v-else class="relative w-full h-screen bg-black">
            <div @click="showFullVideo = false"
                class="absolute z-50 p-0 ml-6 mt-20 text-white bg-opacity-50 rounded-full cursor-pointer hover125 hover:text-blue-400">
                Back
            </div>
            <video :src="'/videos/' + movie.name + '.mp4'" autoplay loop controls
                class="absolute z-40 w-full h-full bg-black" />
        </div>
    </div>
</template>
