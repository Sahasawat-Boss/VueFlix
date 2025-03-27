<script setup>
import Side from "@/components/Side.vue"
import MovieDetails from '@/components/MovieDetails.vue';

import { onMounted } from "vue";
import movies from "./data/movies.json";
import { useMovieStore } from './stores/movie';
import { storeToRefs } from 'pinia';

const useMovie = useMovieStore();
const { movie, showFullVideo } = storeToRefs(useMovie);

onMounted(() => {
  setTimeout(() => movie.value = movies[0][0], 100);
});
</script>

<template>
  <main class="fixed w-full h-screen bg-black">
    <Side />

    <div v-if="!showFullVideo">
      <div class="fixed flex z-20 top-0 right-0 w-full h-[50%] bg-black pl-[120px] bg-clip-border">
        <div class="absolute z-30 h-[600px] left-[120px] w-[77%] right-0 top-0 bg-gradient-to-r from-black via-black" />
        <MovieDetails v-if="movie" :movie="movie" />
        <video v-if="movie" :src="'/videos/' + movie.name + '.mp4'" autoplay muted playsinline loop
          class="absolute z-0 h-[600px] right-0 top-0" />
      </div>
    </div>
  </main>
</template>
