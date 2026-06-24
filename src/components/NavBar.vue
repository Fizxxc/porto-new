<template>
    <nav ref="menuWrapper"
        class="fixed z-40 left-1/2 -translate-x-1/2 bottom-4 md:bottom-auto md:top-4 w-[calc(100%-1rem)] sm:w-[calc(100%-2rem)] md:w-max max-w-[44rem] overflow-x-auto scroll-hidden rounded-full border border-white/30 bg-white/70 p-2 shadow-lg backdrop-blur-xl">
        <ul ref="menuList" class="flex min-w-max items-center gap-2">
            <li v-for="menu in menus" :key="menu.path" :ref="el => (menuRefs[menu.path] = el)"
                class="shrink-0 rounded-full px-4 py-2 text-center text-sm sm:text-base transition-colors duration-300 cursor-pointer select-none" :class="{
                    'bg-primary text-white shadow-md': activeSection === menu.path,
                    'hover:bg-primary hover:text-soft-ivory': activeSection !== menu.path
                }" @click="jumpToSection(menu.path)">
                {{ menu.name }}
            </li>
        </ul>
    </nav>
</template>

<script setup>
import { ref, onMounted, watch, onBeforeUnmount } from 'vue'

const menus = [
    { name: 'Home', path: 'landing' },
    { name: 'About', path: 'about' },
    { name: 'Skill', path: 'skill' },
    { name: 'Projects', path: 'projects' },
    { name: 'Experience', path: 'exp' },
    { name: 'Sertifikat', path: 'certificates' },
]

const activeSection = ref('landing')
const emits = defineEmits(['jumpToSection'])
let observer = null

const jumpToSection = (path) => {
    const section = document.getElementById(path)
    if (section) {
        emits('jumpToSection', path)
    }
}

const menuRefs = {}

onMounted(() => {
    observer = new IntersectionObserver(
        (entries) => {
            const visible = entries
                .filter((entry) => entry.isIntersecting)
                .sort((a, b) => b.intersectionRatio - a.intersectionRatio)

            if (visible.length > 0) {
                activeSection.value = visible[0].target.id
            }
        },
        {
            root: null,
            rootMargin: '-25% 0px -55% 0px',
            threshold: [0.08, 0.2, 0.35]
        }
    )

    menus.forEach((menu) => {
        const section = document.getElementById(menu.path)
        if (section) {
            observer.observe(section)
        }
    })
})

onBeforeUnmount(() => {
    if (observer) observer.disconnect()
})

watch(activeSection, (newSection) => {
    const el = menuRefs[newSection]
    if (el) {
        el.scrollIntoView({ behavior: 'smooth', inline: 'center', block: 'nearest' })
    }
})
</script>

<style scoped>
.scroll-hidden {
    scrollbar-width: none;
    -ms-overflow-style: none;
}

.scroll-hidden::-webkit-scrollbar {
    display: none;
}
</style>
