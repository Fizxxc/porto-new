<template>
    <ul class="flex flex-wrap gap-3 sm:gap-4 justify-start sm:justify-end py-2 text-xl sm:text-2xl">
        <li v-for="contact in contacts" :key="contact.url" class="text-focus-in">
            <a :href="contact.url" target="_blank" rel="noopener noreferrer" :aria-label="contact.label"
                class="group cursor-pointer" :class="classPlus">
                <i :class="contact.icon" />
                <span class="sr-only">{{ contact.label }}</span>
            </a>
        </li>
    </ul>
</template>

<script setup>
defineProps({
    classPlus : String
})
const contacts = [
    { label: 'WhatsApp', icon: 'pi pi-whatsapp', url: 'https://wa.me/6285776568948' },
    { label: 'Instagram', icon: 'pi pi-instagram', url: 'https://instagram.com/fizzx.docx' },
    { label: 'Email', icon: 'pi pi-at', url: 'mailto:fizzx404@gmail.com' }
]
</script>
