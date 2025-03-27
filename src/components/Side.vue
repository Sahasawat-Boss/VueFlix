<!-- src/components/SideNav.vue -->
<script setup>
import { storeToRefs } from "pinia";
import { useMovieStore } from "@/stores/movie";

// Icons
import Magnify from 'vue-material-design-icons/Magnify.vue';
import HomeOutline from 'vue-material-design-icons/HomeOutline.vue';
import TrendingUp from 'vue-material-design-icons/TrendingUp.vue';
import Television from 'vue-material-design-icons/Television.vue';
import MovieOutline from 'vue-material-design-icons/MovieOutline.vue';
import Plus from 'vue-material-design-icons/Plus.vue';

// State
const { showFullVideo } = storeToRefs(useMovieStore());
</script>

<template>
    <nav v-if="!showFullVideo" id="SideNav" class="flex z-40 items-center w-[120px] h-screen bg-black relative">
        <h1 class="gradient-text-green text-6xl font-bold absolute top-0 left-6">VF</h1>
        <div>
            <div class="py-2 mx-10 my-6 hover125">
                <Magnify fillColor="#FFFFFF" :size="40" class="" />
            </div>
            <div class="py-2 mx-10 my-6 hover125 border-b-4 border-b-red-500">
                <HomeOutline fillColor="#FFFFFF" :size="40" class="" />
            </div>
            <div class="py-2 mx-10 my-6 hover125">
                <TrendingUp fillColor="#FFFFFF" :size="40" class="" />
            </div>
            <div class="py-2 mx-10 my-6 hover125">
                <Television fillColor="#FFFFFF" :size="40" class="" />
            </div>
            <div class="py-2 mx-10 my-6 hover125">
                <MovieOutline fillColor="#FFFFFF" :size="40" class="" />
            </div>
            <div class="py-2 mx-10 my-6 hover125">
                <Plus fillColor="#FFFFFF" :size="40" class="" />
            </div>
        </div>
    </nav>
</template>