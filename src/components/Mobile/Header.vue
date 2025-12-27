<script setup lang="ts">
import { ref } from 'vue'
import { BellDot } from 'lucide-vue-next';

const isOpen = ref(false)
</script>

<template>
    <div class="flex justify-between">
        <div>
            <p class="text-gray-400">Localtion</p>
            <div class="relative">
                <button @click="isOpen = !isOpen" class="flex w-full items-center justify-between rounded-md
        py-2 text-sm focus:outline-none focus:ring-1 focus:ring-white">
                    <span class="mr-2">Option 1</span>
                    <svg class="h-4 w-4 text-neutral-400" viewBox="0 0 24 24" fill="none">
                        <path d="M6 9l6 6 6-6" stroke="currentColor" stroke-width="2" />
                    </svg>
                </button>

                <ul v-if="isOpen" class="absolute z-10 mt-1 w-full rounded-md border border-gray-200">
                    <li class="cursor-pointer px-3 py-2 text-sm hover:bg-neutral-100">Option1</li>
                    <li class="cursor-pointer px-3 py-2 text-sm hover:bg-neutral-100">Option2</li>
                    <li class="cursor-pointer px-3 py-2 text-sm hover:bg-neutral-100">Option3</li>
                </ul>
            </div>
        </div>
        <div class="flex items-center">
            <BellDot />
        </div>
    </div>
</template>