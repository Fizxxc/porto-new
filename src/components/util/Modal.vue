<template>
    <Transition name="modal">
        <div class="fixed inset-0 z-50 flex h-dvh w-full items-center justify-center overflow-y-auto px-4 py-6 box-border backdrop-blur-sm"
            @click="closeModal" v-if="isActive">
            <div @click.stop
                class="max-h-[90dvh] w-full max-w-3xl overflow-y-auto rounded-[2rem] border border-white/40 bg-white/75 p-5 shadow-2xl backdrop-blur-md sm:p-8">
                <div class="flex items-start justify-between gap-4">
                    <h1 class="fluid-heading capitalize font-bold safe-text">
                        {{ data.name }}
                    </h1>
                    <button type="button" class="flex h-10 w-10 shrink-0 items-center justify-center rounded-full bg-primary text-soft-ivory" @click="closeModal" aria-label="Close modal">
                        <i class="pi pi-times"></i>
                    </button>
                </div>
                <div class="flex-1 flex flex-col justify-center gap-y-4 pt-5">
                    <p class="text-base sm:text-lg leading-8 safe-text">{{ data.description }}</p>
                    <div class="flex flex-wrap gap-3">
                        <span class="block bg-primary text-soft-ivory text-center rounded-full px-4 py-1 text-sm safe-text"
                            v-for="t in data.tech" :key="t">
                            {{ t }}
                        </span>
                    </div>
                    <div class="flex flex-row flex-wrap gap-4 justify-end">
                        <p class="bg-yellow-400 p-2 w-max rounded-full border px-4">{{ data.year }}</p>
                        <a v-if="data.link" :href="data.link" target="_blank" rel="noopener noreferrer"
                            class="bg-primary text-soft-ivory hover:bg-red-800 transition-colors duration-500 h-10 w-10 rounded-full flex justify-center items-center">
                            <i class="pi pi-arrow-up-right"></i>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </Transition>
</template>

<script setup>
defineProps({
    data: {
        default: null
    },
    isActive: Boolean
})

const emits = defineEmits(['closeModal'])
const closeModal = () => {
    emits('closeModal', false)
}
</script>

<style scoped>
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.5s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}
</style>
