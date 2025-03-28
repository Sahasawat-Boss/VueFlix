<template>
    <!-- Mobile toggle button (hamburger) -->
    <div class="md:hidden fixed top-6 left-6 z-50">
        <button @click="toggleMenu" class="text-white text-3xl hover125">☰</button>
    </div>

    <!-- Sidebar -->
    <div id="SideNav" class="fixed top-0 left-0 w-fit p-2 h-screen bg-black z-40 transition-transform duration-300"
        :class="[
            isOpen ? 'translate-x-0' : '-translate-x-full',
            'w-[120px] md:translate-x-0 md:flex md:flex-col'
        ]">
        <div class="flex flex-col justify-between h-full">
            <!-- Top section: Icons -->
            <div class="mt-20 flex flex-col gap-6 text-white/35">
                <div class="hover125 text-red-600">
                    <HomeOutline size="40" />
                </div>
                <div class="hover125">
                    <Magnify size="30" />
                </div>
                <div class="hover125">
                    <TrendingUp size="30" />
                </div>
                <div class="hover125">
                    <Television size="30" />
                </div>
                <div class="hover125">
                    <MovieOutline size="30" />
                </div>
                <div class="hover125">
                    <Plus size="30" />
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