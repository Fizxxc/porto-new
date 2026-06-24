<template>
    <section class="px-4 lg:px-16 py-10 lg:py-24 min-h-screen">
        <div class="flex flex-col gap-y-10">
            <div class="space-y-3">
                <p class="uppercase tracking-[0.4em] text-sm text-warm-gray">Capabilities</p>
                <h1 class="text-5xl lg:text-8xl">Skills</h1>
            </div>

            <div class="grid lg:grid-cols-[1.5fr_1fr] gap-6">
                <div class="rounded-3xl bg-primary text-soft-ivory p-6 lg:p-8">
                    <h2 class="text-3xl font-semibold mb-6">Hard Skills</h2>
                    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-3">
                        <div v-for="skill in hardSkills" :key="skill" class="rounded-2xl border border-soft-ivory/20 p-4 bg-white/5">
                            {{ skill }}
                        </div>
                    </div>
                </div>

                <div class="rounded-3xl bg-soft-ivory p-6 lg:p-8">
                    <h2 class="text-3xl font-semibold mb-6">Soft Skills</h2>
                    <div class="space-y-3">
                        <div v-for="skill in softSkills" :key="skill" class="rounded-2xl bg-white/70 p-4 border border-primary/10">
                            {{ skill }}
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
const hardSkills = [
    'Adobe After Effects',
    'Adobe Illustrator',
    'Adobe Premiere Pro',
    'Adobe Photoshop',
    'Adobe Audition',
    'Canva',
    'OBS Studio',
    'Vmix',
    'CapCut',
    'Alight Motion',
    'Microsoft Word',
    'Microsoft Excel',
]

const softSkills = [
    'Love Challenge',
    'Easy To Adapt',
    'Team Work',
    'Adaptability',
]
</script>
