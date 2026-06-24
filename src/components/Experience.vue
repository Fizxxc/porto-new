<template>
    <section class="section-shell min-h-svh">
        <div class="flex flex-col gap-y-10">
            <div class="flex flex-col gap-y-3">
                <p class="section-kicker text-warm-gray">From CV</p>
                <h1 class="fluid-title safe-text">Experience</h1>
            </div>

            <div class="relative grid gap-5 lg:gap-6">
                <article v-for="(exp, index) in experiences" :key="`${exp.date}-${exp.role}`"
                    class="grid gap-4 rounded-[2rem] border border-primary/10 bg-white/70 p-5 shadow-sm md:grid-cols-[12rem_1fr] lg:grid-cols-[15rem_1fr] lg:p-6">
                    <div class="min-w-0 md:text-right">
                        <span class="inline-flex h-9 w-9 items-center justify-center rounded-full bg-primary text-soft-ivory text-sm font-semibold md:ml-auto">
                            {{ String(index + 1).padStart(2, '0') }}
                        </span>
                        <p class="pt-4 text-xs sm:text-sm uppercase tracking-widest text-warm-gray safe-text">{{ exp.date }}</p>
                        <h2 class="text-xl sm:text-2xl font-semibold pt-1 safe-text">{{ exp.role }}</h2>
                    </div>

                    <div class="relative min-w-0 md:border-l md:border-primary/10 md:pl-6">
                        <p class="font-semibold text-primary/80 safe-text">{{ exp.place }}</p>
                        <p class="pt-4 leading-7 text-justify safe-text">{{ exp.description }}</p>
                        <div class="flex flex-wrap gap-2 pt-5">
                            <span v-for="tag in exp.tags" :key="tag" class="px-4 py-1 bg-soft-ivory rounded-full text-sm safe-text">
                                {{ tag }}
                            </span>
                        </div>
                    </div>
                </article>
            </div>
        </div>
    </section>
</template>

<script setup>
const experiences = [
    {
        date: 'March 11, 2026',
        role: 'Visual Operator',
        place: 'MetschoRama Event - Metland School Cibitung, Bekasi',
        description: 'Visual Operator for the MetschoRama event, supporting the event flow through visual operation and stage-screen coordination.',
        tags: ['Visual Operator', 'Event Visual', 'School Event'],
    },
    {
        date: 'December 31, 2025',
        role: 'Documentation Crew, Visual Editor & Audio-Visual (VA)',
        place: 'Metland Bergoyang Event - Metland School Cibitung, Bekasi',
        description: 'Documentation, visual editor, and sound operator crew for the Metland Bergoyang event.',
        tags: ['Documentation', 'Visual Editing', 'Sound Operator'],
    },
    {
        date: 'November 22, 2025',
        role: 'Audio-Visual (AV)',
        place: 'Grand Final Abang & Mpok Milenia - Milenia Metland Cibitung, Bekasi',
        description: 'Sound operator and sound editor for the Grand Final Abang & Mpok Milenia event.',
        tags: ['Audio-Visual', 'Sound Editing', 'Sound Operator'],
    },
    {
        date: 'October 11, 2025',
        role: 'Audio-Visual (AV), VJ, Documentation Crew',
        place: 'Warna Warni Nusantara School Ambassador Event - Milenia Metland Cibitung, Bekasi',
        description: 'Handled audio-visual and documentation crew responsibilities for the school ambassador event.',
        tags: ['AV', 'VJ', 'Documentation'],
    },
    {
        date: 'August 30, 2025',
        role: 'Audio-Visual (AV), VJ, Documentation Crew',
        place: 'Sambut Generasi Cinta Prestasi School Event - Milenia Metland Cibitung, Bekasi',
        description: 'Audio-visual, VJ, and documentation crew for the Sambut Generasi Cinta Prestasi school event.',
        tags: ['AV', 'VJ', 'Documentation'],
    },
    {
        date: 'May 24, 2025',
        role: 'Audio-Visual (AV), VJ, Documentation Crew',
        place: 'Metschoo Fest School Event - Metland School Cibitung, Bekasi',
        description: 'Audio-visual and documentation crew for the Metschoo Fest school event.',
        tags: ['AV', 'VJ', 'Documentation'],
    },
    {
        date: 'February 14, 2025',
        role: 'Maheswara Maheswari Grand Final',
        place: 'Metropolitan Mall Cileungsi, Bogor',
        description: 'Participant of Maheswara Maheswari Metland School Grand Final.',
        tags: ['Finalist', 'Personal Branding', 'School Representative'],
    },
]
</script>
