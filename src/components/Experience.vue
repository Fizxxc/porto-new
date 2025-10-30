<template>
    <section class="px-4 lg:px-16 py-10 lg:py-8 min-h-screen">
        <div class="flex flex-col gap-y-24">
            <h1 class="text-5xl lg:text-8xl">Experience</h1>
            <div class="grid lg:grid-cols-2 gap-2 lg:gap-4" v-for="exp in experiences">
                <div class="flex flex-row gap-x-4">
                    <h1 class="slr text-3xl border h-max p-2 bg-primary text-soft-ivory rounded-md">
                       {{ exp.job }}
                    </h1>
                    <div>
                        <h2 class="text-4xl lg:text-5xl">{{ exp.role }}</h2>
                        <h3 class="pt-2 lg:text-2xl">{{ exp.place }}</h3>
                        <h4 class="pt-2">{{ exp.date }}</h4>
                        <p class="pt-6 text-justify">
                            {{ exp.description }}
                        </p>
                        <div class="flex flex-wrap gap-2 pt-4">
                            <div v-for="t in exp.tech" class="px-4 py-1 bg-yellow-400 rounded-full">
                                {{ t }}
                            </div>
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
        role: 'Desainer Grafis',
        place: 'Smk Metland Cibitung',
        date: '2024 - Present',
        description: `Mendesain identitas visual dan aset digital (logo, banner, materi pemasaran), membuat UI mockup di Figma, memproduksi ilustrasi dan layout untuk materi cetak menggunakan Adobe Illustrator & InDesign, serta menyiapkan file siap-cetak sambil berkolaborasi dengan tim produk untuk konsistensi brand.`,
        tech: ['figma', 'photoshop', 'illustrator', 'lightroom'],
        job: 'internship'
    }
]
</script>
