<template>
    <!-- Mobile toggle button (hamburger) -->
    <div class="md:hidden fixed top-4 left-4 z-50">
        <button @click="toggleMenu" class="text-white text-3xl">☰</button>
    </div>

    <!-- Sidebar -->
    <div id="SideNav" class="fixed top-0 left-0 w-fit p-2 h-screen bg-black z-40 transition-transform duration-300"
        :class="[
            isOpen ? 'translate-x-0' : '-translate-x-full',
            'w-[120px] md:translate-x-0 md:flex md:flex-col'
        ]">
        <div class="flex flex-col justify-between h-full">
            <!-- Top section: Icons -->
            <div class="mt-12">
                <div class="py-2 mx-4 my-6 border-b-4 border-b-red-700 hover125">
                    <HomeOutline fillColor="#FFFFFF" :size="36" />
                </div>
                <div class="py-2 mx-4 my-6 hover125">
                    <Magnify fillColor="#bbbb" :size="36" />
                </div>
                <div class="py-2 mx-4 my-6 hover125">
                    <TrendingUp fillColor="#bbbb" :size="36" />
                </div>
                <div class="py-2 mx-4 my-6 hover125">
                    <Television fillColor="#bbbb" :size="36" />
                </div>
                <div class="py-2 mx-4 my-6 hover125">
                    <MovieOutline fillColor="#bbbb" :size="36" />
                </div>
                <div class="py-2 mx-4 my-6 hover125">
                    <Plus fillColor="#bbbb" :size="36" />
                </div>
            </div>

            <!-- Bottom section: Logo -->
            <div class="mb-6 text-center">
                <h1 class="gradient-text-green text-4xl md:text-6xl font-bold hover110">VF</h1>
            </div>
        </div>

    </div>
</template>

<script setup>
import { ref } from 'vue'

import Magnify from 'vue-material-design-icons/Magnify.vue'
import HomeOutline from 'vue-material-design-icons/HomeOutline.vue'
import TrendingUp from 'vue-material-design-icons/TrendingUp.vue'
import Television from 'vue-material-design-icons/Television.vue'
import MovieOutline from 'vue-material-design-icons/MovieOutline.vue'
import Plus from 'vue-material-design-icons/Plus.vue'

const isOpen = ref(false)
const toggleMenu = () => {
    isOpen.value = !isOpen.value
}
</script>