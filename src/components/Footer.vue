<template>
    <footer
        class="w-full bg-black text-white pt-8 pb-16 px-4 md:px-12 flex flex-col md:flex-row items-center justify-between gap-4">
        <!-- Left: Links -->
        <div class="flex flex-col md:flex-row items-center gap-4">
            <a href="https://github.com/Sahasawat-Boss" target="_blank" rel="noopener noreferrer"
                class="hover110 gradient-text-green font-bold tracking-wider">
                GitHub
            </a>
            <a href="https://bossbsynth.com/" target="_blank" rel="noopener noreferrer" class="hover110 gradient-text-green font-bold tracking-wider">
                bossbsynth.com
            </a>
        </div>

        <!-- Right: Copyright -->
        <div class="text-sm text-gray-400 text-center md:text-right font-semibold tracking-wider">
            © {{ new Date().getFullYear() }} Boss BSynth. All rights reserved.
        </div>
    </footer>
</template>