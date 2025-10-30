<template>
    <section class="px-4 lg:px-16 py-10 lg:py-24 min-h-screen relative">
        <div class="flex flex-col gap-y-8">
            <!-- Title -->
            <h1 class="text-5xl lg:text-8xl" id="p-heading">Projects</h1>
            <!-- Wrapper -->
            <div class="grid gap-8 md:grid-cols-2">
                <!-- Project -->
               <div v-for="p in projects" :key="p.name" class="flex flex-col gap-y-4">
                <!-- Image -->
                    <div class="w-full rounded-lg overflow-hidden shadow-sm cursor-pointer" @click="sendProject(p)">
                        <img :src="p.image" alt="project-image" class="w-full h-full object-bottom">
                    </div>
                    <!-- Info -->
                    <div class="flex flex-row">
                       <div class="w-full space-y-4">
                         <h1 class="capitalize font-semibold text-3xl">
                            {{ p.name }}
                        </h1>
                        <h3>
                            {{ p.year }}
                        </h3>
                       </div>
                       <button class="h-10 w-10 shrink-0" v-if="p.link">
                            <a :href="p.link" target="_blank"
                                class="bg-primary text-soft-ivory hover:bg-light-gray transition-color hover:text-primary duration-500 h-full w-full rounded-full flex justify-center items-center">
                                <i class="pi pi-arrow-up-right"></i>
                            </a>
                        </button>
                        <p v-else class="bg-red-700 flex items-center text-center text-xs rounded-md h-max py-1 px-2 text-soft-ivory">
                           Deactivate
                        </p>
                    </div>
               </div>
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
    console.log(data);
     
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
