<template>
    <button v-show="showButton" @click="scrollToTop"
        class="fixed px-1 pt-1 hover110  bottom-7.5 right-4.5 z-50 bg-blue-600 hover:bg-blue-500 text-white  rounded-full shadow-lg transition-all duration-300">
        <i class="pi pi-arrow-circle-up" style="font-size: 1.5rem"></i>
    </button>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const showButton = ref(false)

const handleScroll = () => {
    showButton.value = window.scrollY > 150
}

const scrollToTop = () => {
    window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => {
    window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
})
</script>