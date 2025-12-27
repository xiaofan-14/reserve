<script setup lang="ts">
import Header from '../components/Mobile/Header.vue';
import { Search } from 'lucide-vue-next';
import { SlidersHorizontal } from 'lucide-vue-next';
import { ref } from 'vue'
import { MapPin } from 'lucide-vue-next';

const activeMenu = ref('House');

const menuList = [
    { name: 'House' },
    { name: 'Apartment' },
    { name: 'Hotel' },
    { name: 'Villa' },
    { name: 'Cottage' },
]

function setActiveMenu(name: string) {
    activeMenu.value = name;
}
</script>

<template>
    <div class="container px-4 py-2">
        <Header />
        <div>
            <div class="py-1 flex justify-between items-center gap-4">
                <div class="bg-gray-100 flex px-3 py-1 gap-1 items-center w-full rounded-lg ">
                    <Search />
                    <input type="text" placeholder="输入地址" class="
                    h-9 w-full rounded-md
                    border-none px-3
                    text-sm text-neutral-900
                    placeholder:text-neutral-400
                    transition-colors
                    focus:outline-none focus:ring-1 focus:ring-gray-400
                    disabled:cursor-not-allowed disabled:bg-neutral-50 
                    disabled:text-neutral-400
                " />
                </div>
                <div class="bg-gradient-to-b from-cyan-300 to-blue-400 p-2 rounded-lg">
                    <SlidersHorizontal class="text-white" />
                </div>
            </div>
            <div class="mt-3 flex gap-3 overflow-x-auto pb-2">
                <div v-for="(item, idx) in menuList" :key="idx" @click="setActiveMenu(item.name)"
                    class="w-fit bg-gradient-to-b rounded-lg p-2" :class="activeMenu === item.name
                        ? 'bg-gradient-to-b from-cyan-300 to-blue-400 text-white shadow-lg shadow-cyan-200/50'
                        : 'bg-gray-50 text-gray-400'">
                    {{ item.name }}
                </div>
            </div>
            <div class="mt-3">
                <div class="flex justify-between">
                    <p class="text-start text-black">Near from you</p>
                    <p class="text-end text-gray-500">see more</p>
                </div>
                <div class="mt-2 flex gap-4 overflow-x-auto pb-2">
                    <div v-for="idx in 5" :key="idx" class="w-50 h-60 rounded-3xl border border-red-500 flex flex-col items-center justify-center p-2 shrink-0">
                        <p class="flex-1 flex justify-end ">
                        <div class="flex items-center gap-1 bg-gray-200 rounded-full h-fit p-1 px-2 text-xs">
                            <MapPin class="w-4" />
                            <span>1.8KM</span>
                        </div>
                        </p>
                        <div class="flex-2 w-full p-2 flex flex-col justify-end gap-1 px-2">
                            <p>地址</p>
                            <p>联系人</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>