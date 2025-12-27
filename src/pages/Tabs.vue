<script setup lang="ts">
import { ref } from 'vue'

const activeTab = ref('tab1')

function setActiveTab(tab: string) {
    activeTab.value = tab;
}
</script>

<template>
    <div class="container m-auto mt-4 p-4 border border-red-200">
        <div class="flex gap-4">
            <div @click="setActiveTab('tab1')" class="cursor-pointer w-fit p-1 text-sm rounded-md" :class="activeTab === 'tab1'
                ? 'bg-gradient-to-b from-cyan-300 to-blue-400 text-white shadow-lg shadow-cyan-200/50'
                : 'shadow-lg bg-gray-200 text-gray-800'">tab 1</div>
            <div @click="setActiveTab('tab2')" class="cursor-pointer w-fit p-1 text-sm rounded-md" :class="activeTab === 'tab2'
                ? 'bg-gradient-to-b from-cyan-300 to-blue-400 text-white shadow-lg shadow-cyan-200/50'
                : 'shadow-lg bg-gray-200 text-gray-800'">
                tab 2
            </div>
            <div @click="setActiveTab('tab3')" class="cursor-pointer w-fit p-1 text-sm rounded-md" :class="activeTab === 'tab3'
                ? 'bg-gradient-to-b from-cyan-300 to-blue-400 text-white shadow-lg shadow-cyan-200/50'
                : 'shadow-lg bg-gray-200 text-gray-800'">
                tab 3
            </div>
        </div>
        <div class="bg-gray-200 shadow mt-4 p-4 rounded-md">
            <div v-if="activeTab === 'tab1'">tab1 内容区域</div>
            <div v-if="activeTab === 'tab2'">tab2 内容区域</div>
            <div v-if="activeTab === 'tab3'">tab3 内容区域</div>
        </div>
    </div>
</template>