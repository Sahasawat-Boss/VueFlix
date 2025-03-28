<script setup>
import SideNav from "@/components/SideNav.vue";
import MovieDetails from "@/components/MovieDetails.vue";
import VideoCarousel from "./components/VideoCarousel.vue";

// Icons ===============================================================
import ChevronLeft from 'vue-material-design-icons/ChevronLeft.vue';
// Icons ===============================================================

import { onMounted } from "vue";
import movies from "./data/movies.json";
import { useMovieStore } from "./stores/movie";
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
      <div class="relative w-full h-[50vh] bg-black overflow-hidden">
        <div class="absolute z-30 h-full w-full bg-gradient-to-r from-black via-black" />

        <MovieDetails v-if="movie" :movie="movie" class="absolute z-50 left-[130px] top-0 px-4 pt-20 w-[80%]" />


        <video v-if="movie" :src="'/videos/' + movie.name + '.mp4'" autoplay loop muted
          class="absolute z-0 top-0 right-0 h-full w-full object-cover" />
      </div>

<!-- Bottom Section: Carousels -->
<div class="relative w-full h-[50vh] overflow-y-auto px-4 md:px-6">
        <VideoCarousel class="pb-14 pt-14" category="Popular Movies" :movies="movies[0]" />
        <VideoCarousel class="pb-14" category="Horror Movies" :movies="movies[1]" />
        <VideoCarousel class="pb-32" category="Featured Movies" :movies="movies[2]" />
      </div>

      <!-- Gradient overlay -->
      <!--<div class="absolute z-20 h-[50vh] w-full bottom-0 bg-gradient-to-t from-black via-black pointer-events-none" /> -->
    </div>

    <!-- Full-screen video view -->
    <div v-else class="relative w-full h-screen bg-black">
      <div
        @click="showFullVideo = false"
        class="absolute z-50 p-1 m-6 bg-white bg-opacity-50 rounded-full cursor-pointer hover125"
      >
        <ChevronLeft fillColor="#000000" :size="38" />
      </div>
      <video
        :src="'/videos/' + movie.name + '.mp4'"
        autoplay
        loop
        controls
        class="absolute z-0 w-full h-full object-cover"
      />
    </div>
  </div>
</template>
