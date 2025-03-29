<template>
    <div class="min-w-[1200px] relative">
        <!-- Category Title -->
        <div class="flex justify-between mr-6">
            <div class="flex items-center font-semibold text-white text-2xl cursor-pointer fade-in-left">
                {{ category }}
            </div>
        </div>

        <!-- Carousel Section -->
        <Carousel ref="carousel" v-model="currentSlide" :items-to-show="9" :items-to-scroll="1" :wrap-around="true"
            :transition="450" snapAlign="start" class="bg-transparent fade-in-up">
            <!-- Slide for each movie -->
            <Slide v-for="(slide, index) in movies" :key="slide.name"
                class="flex flex-col items-center object-cover text-white bg-transparent">
                <div @click="fullScreenVideo(index)" class="object-cover h-4/5 hover:brightness-125 hover"
                    :class="[
                        currentSlide === index
                            ? 'scale-105 border-2 border-blue-400 shadow-xl'
                            : 'opacity-50',
                        'transition-all duration-300 ease-in-out'
                    ]">
                    <img style="user-select: none" class="pointer-events-none h-full w-full"
                        :src="'/images/' + slide.name + '.png'" alt="movie poster" />
                </div>
                <div class="text-sm text-center pt-2">{{ slide.name }}</div>
            </Slide>

            <!-- Carousel Controls -->
            <template #addons>
                <Navigation  class="scale-150"/>
            </template>
        </Carousel>
    </div>
</template>

<script setup>
import { ref, toRefs } from "vue";
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Navigation } from "vue3-carousel";

import { useMovieStore } from "../stores/movie";
import { storeToRefs } from "pinia";
const useMovie = useMovieStore();
const { movie, showFullVideo } = storeToRefs(useMovie);

const props = defineProps({ category: String, movies: Array });
const { movies, category } = toRefs(props);

let currentSlide = ref(0);

// Set current movie and open full video view
const fullScreenVideo = (index) => {
    currentSlide.value = index;
    movie.value = movies.value[index];
    //setTimeout(() => (showFullVideo.value = false));
    setTimeout(() => (showFullVideo.value = true), 600);
};
</script>

<style>
.carousel__prev,
.carousel__next,
.carousel__prev:hover,
.carousel__next:hover {
    color: white;
}
</style>