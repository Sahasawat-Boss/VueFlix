<template>
    <nav class="flex items-center justify-between top-0 left-0 w-full z-[99] bg-black shadow-xl px-6 py-1.5 md:py-2">
        <!-- Logo -->
        <router-link to="/" class="gradient-text-green text-3xl md:text-4xl font-bold hover110 fade-in-left">
            VF
            <span class="text-sm ">[Demo]</span>
        </router-link>

        <!-- To https://bossbsynth.com/-->
        <div class="flex items-center">
            <a href="https://bossbsynth.com/" target="_blank" rel="noopener noreferrer"
                class="gradient-text-green text-xs font-semibold hover110 fade-in-right">
                <span class="text-blue-400/85"><i class="pi pi-spin pi-globe" style="font-size: 0.7rem"></i></span>

                bossbsynth.com
            </a>
        </div>

    </nav>
</template>