<template>
    <section class="section-shell min-h-svh relative">
        <div class="flex flex-col gap-y-9">
            <div class="space-y-3">
                <p class="section-kicker text-warm-gray">Selected Work</p>
                <h1 class="fluid-title safe-text" id="p-heading">Projects</h1>
            </div>

            <div class="grid gap-7 md:grid-cols-2">
               <article v-for="p in projects" :key="p.name" class="group flex min-w-0 flex-col gap-y-4 rounded-[2rem] bg-white/70 p-3 sm:p-4 shadow-sm border border-primary/10">
                    <button type="button" class="w-full overflow-hidden rounded-[1.5rem] bg-soft-ivory text-left cursor-pointer" @click="sendProject(p)">
                        <img :src="p.image" :alt="`${p.name} project image`" class="aspect-[4/3] w-full object-cover object-center transition duration-500 group-hover:scale-105">
                    </button>
                    <div class="flex flex-col gap-4 sm:flex-row sm:items-start">
                       <div class="w-full min-w-0 space-y-2">
                         <h2 class="capitalize font-semibold text-2xl sm:text-3xl safe-text">
                            {{ p.name }}
                        </h2>
                        <p class="text-warm-gray safe-text">
                            {{ p.year }}
                        </p>
                       </div>
                       <a v-if="p.link" :href="p.link" target="_blank" rel="noopener noreferrer"
                            class="bg-primary text-soft-ivory hover:bg-light-gray transition-colors hover:text-primary duration-500 h-11 w-11 rounded-full flex shrink-0 justify-center items-center">
                            <i class="pi pi-arrow-up-right"></i>
                        </a>
                        <p v-else class="bg-primary/80 flex shrink-0 items-center justify-center text-center text-xs rounded-full h-max py-2 px-4 text-soft-ivory">
                           Preview
                        </p>
                    </div>
               </article>
            </div>
        </div>
    </section>
</template>

<script setup>
import ps from '@/assets/img/projects/posterr.png'
import ps3 from '@/assets/img/projects/posterr3.png'
import ps2 from '@/assets/img/projects/posterr2.jpg'
import ps4 from '@/assets/img/projects/1.png'

const emits = defineEmits(['sendProject'])

const sendProject = (data)=>{
    emits('sendProject',data)
}

const projects = [
    {
        name: "valentine day",
        year: 2025,
        description: "Self-project, a Valentine's Day poster collection application featuring romantic designs and interactive user experience",
        tech: [
            'Photoshop',
            'Illustrator',
        ],
        image: ps,
        link: null
    },
    {
        name: "Energy Drink",
        year: 2025,
        description: "Self-project, an energy drink ordering application",
        tech: [
            'Photoshop',
        ],
        image: ps2,
        link: null
    },
    {
        name: "Geopelia striata Photography",
        year: 2025,
        description: "Self-project, desain fotografi burung Geopelia striata (perkutut), menampilkan keindahan dan detail dari burung perkutut dengan teknik fotografi yang estetik",
        tech: [
            'Sony a6400',
            'Lightroom',
        ],
        image: ps4,
        link: null
    },
    {
        name: "Guerlain Parfume",
        year: 2025,
        description: "Self-project, desain branding dan kemasan untuk parfum Guerlain, menampilkan konsep visual, inspirasi aroma, dan materi promosi",
        tech: [
            'Photoshop',
        ],
        image: ps3,
        link: null
    },
]
</script>
