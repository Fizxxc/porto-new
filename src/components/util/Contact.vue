<template>
    <ul class="inline-flex gap-x-6 justify-end py-4 text-2xl">
        <li v-for="contact in contacts" :key="contact.url"
            class="cursor-pointer hover:text-red-600 transition-colors duration-300 text-focus-in" :class="classPlus">
            <a :href="contact.url" target="_blank" :aria-label="contact.label">
                <i :class="contact.icon" />
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
