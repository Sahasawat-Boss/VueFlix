<template>
    <!-- Full screen container -->
    <div class="min-h-screen flex flex-col bg-black text-white overflow-y-scroll">
        <TopNav/>

        <!-- Centered content -->
        <div class="flex flex-grow flex-col justify-center items-center text-center px-4">
            <h1 class="text-4xl font-bold mb-4 gradient-text-green">About This App</h1>

            <p class="text-lg max-w-xl px-12 mb-6 text-gray-300">
                This is a
                <span class="text-blue-400 font-semibold">demo version</span> of
                <span class="text-green-400"> VF</span> —
                <span class="text-white font-semibold">a Vue-powered movie preview platform developed by
                    BossBSynth</span>.
            </p>

            <div class="flex flex-col md:flex-row gap-4">
                <!-- Home Link Button with green gradient -->
                <router-link to="/"
                    class="bg-gradient-to-r from-green-700 to-green-400 hover:from-green-600 hover110 px-6 py-2 rounded-full text-white transition">
                    ← Go Back Home
                </router-link>

                <!-- External Link Button with blue-to-indigo gradient -->
                <a href="https://bossbsynth.com/" target="_blank" rel="noopener noreferrer"
                    class="bg-gradient-to-r from-blue-700 to-indigo-500 hover:from-blue-400 hover110 px-6 py-2 rounded-full text-white transition">
                    Visit BossBSynth.com ↗
                </a>
            </div>
        </div>
        <Footer/>
    </div>
</template>

<script setup>
import TopNav from '@/components/TopNav.vue';
import Footer from '@/components/Footer.vue';

</script>