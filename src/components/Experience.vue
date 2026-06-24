<template>
    <section class="px-4 lg:px-16 py-10 lg:py-24 min-h-screen">
        <div class="flex flex-col gap-y-10">
            <div class="flex flex-col gap-y-3">
                <p class="uppercase tracking-[0.4em] text-sm text-warm-gray">From CV</p>
                <h1 class="text-5xl lg:text-8xl">Experience</h1>
            </div>

            <div class="relative grid gap-6">
                <div v-for="exp in experiences" :key="`${exp.date}-${exp.role}`" class="grid lg:grid-cols-[220px_1fr] gap-4 lg:gap-8">
                    <div class="lg:text-right">
                        <p class="text-sm uppercase tracking-widest text-warm-gray">{{ exp.date }}</p>
                        <h2 class="text-2xl font-semibold pt-1">{{ exp.role }}</h2>
                    </div>

                    <div class="relative rounded-3xl bg-white/70 border border-primary/10 p-6 shadow-sm">
                        <div class="hidden lg:block absolute -left-[30px] top-8 h-4 w-4 rounded-full bg-primary"></div>
                        <div class="hidden lg:block absolute -left-[23px] top-12 h-full w-[2px] bg-primary/20"></div>

                        <p class="font-semibold text-primary/80">{{ exp.place }}</p>
                        <p class="pt-4 leading-7 text-justify">{{ exp.description }}</p>
                        <div class="flex flex-wrap gap-2 pt-5">
                            <span v-for="tag in exp.tags" :key="tag" class="px-4 py-1 bg-soft-ivory rounded-full text-sm">
                                {{ tag }}
                            </span>
                        </div>
                    </div>
                </div>
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
