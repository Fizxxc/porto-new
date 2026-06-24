<template>
    <section class="section-shell min-h-svh">
        <div class="flex flex-col gap-y-10">
            <div class="space-y-3">
                <p class="section-kicker text-warm-gray">Capabilities</p>
                <h1 class="fluid-title safe-text">Skills</h1>
            </div>

            <div class="grid gap-6 xl:grid-cols-[1.55fr_1fr]">
                <div class="rounded-[2rem] bg-primary text-soft-ivory p-5 sm:p-8 shadow-xl">
                    <div class="flex flex-col gap-2 sm:flex-row sm:items-end sm:justify-between">
                        <h2 class="text-2xl sm:text-3xl font-semibold">Hard Skills</h2>
                        <p class="text-sm text-soft-ivory/60">Tools & production workflow</p>
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-3 pt-6">
                        <div v-for="skill in hardSkills" :key="skill" class="rounded-2xl border border-soft-ivory/20 p-4 bg-white/5 safe-text">
                            {{ skill }}
                        </div>
                    </div>
                </div>

                <div class="rounded-[2rem] bg-soft-ivory p-5 sm:p-8 shadow-sm">
                    <h2 class="text-2xl sm:text-3xl font-semibold mb-6">Soft Skills</h2>
                    <div class="grid gap-3 sm:grid-cols-2 xl:grid-cols-1">
                        <div v-for="skill in softSkills" :key="skill" class="rounded-2xl bg-white/80 p-4 border border-primary/10 safe-text">
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
