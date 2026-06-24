<template>
    <section class="section-shell min-h-svh flex items-stretch pt-24 md:pt-28 pb-28 md:pb-16">
        <div class="min-h-[calc(100svh-9rem)] w-full grid content-between gap-12">
            <div class="flex max-w-6xl flex-col gap-y-5 box-border">
                <p class="text-base sm:text-lg lg:text-2xl split text-warm-gray safe-text">Portfolio of</p>
                <h1 class="fluid-title split safe-text">Hafiz<br>Al Fariz</h1>
                <h2 class="badge w-fit max-w-full rounded-full bg-soft-ivory px-4 py-2 text-sm sm:text-base lg:text-2xl leading-snug safe-text">
                    VCD Student • Motion Graphic • Visual Operator
                </h2>
            </div>

            <div class="flex flex-col items-stretch gap-5 sm:items-end">
                <h3 class="fluid-subtitle split max-w-4xl text-left sm:text-end safe-text">
                    Turning simple shapes <br class="hidden sm:block"> into meaningful visual stories.
                </h3>
                <Contact
                    :class-plus="'flex justify-center items-center h-11 w-11 sm:h-12 sm:w-12 rounded-full bg-soft-ivory hover:bg-primary hover:text-soft-ivory transition-colors duration-500'" />
            </div>
        </div>
    </section>
</template>

<script setup>
import { onMounted } from 'vue';
import Contact from './util/Contact.vue';
import { SplitText } from 'gsap/SplitText';
import gsap from 'gsap';

onMounted(() => {
    let split = SplitText.create(".split", {
        type: "words,lines",
        mask: "lines",
    })

    gsap.from('.badge', {
        x: -60,
        opacity: 0,
        duration: 1,
        ease: 'power3.out'
    })
    gsap.from(split.lines, {
        y: 80,
        opacity: 0,
        duration: 1,
        stagger: 0.16,
        ease: 'power3.out'
    })
})

</script>
