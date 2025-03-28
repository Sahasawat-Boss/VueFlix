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

<template>
    <!-- Mobile toggle button (hamburger) -->
    <div class="flex md:hidden fixed top-14 left-5 z-40 fade-in-left">
        <button @click="toggleMenu" class="text-white text-2xl hover125">☰</button>
    </div>

    <!-- Sidebar -->
    <div id="SideNav" class="fixed top-0 left-0 w-fit p-3 h-screen bg-black z-30 transition-transform duration-300"
        :class="[
            isOpen ? 'translate-x-0' : '-translate-x-full',
            'w-[120px] md:translate-x-0 md:flex md:flex-col'
        ]">
        <div class="flex flex-col h-full fade-in-left">
            <!-- Top section: Icons -->
            <div class="mt-28 flex justify-center items-center flex-col gap-6 text-white/35">
                <div class="flex flex-col items-center space-y-1 text-red-500 hover125">
                    <HomeOutline :size="40" />
                    <div class="w-full h-0.5 bg-red-500"></div> <!-- This is the underline -->
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
        </div>

    </div>
</template>

