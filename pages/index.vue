<style>
    .bg-spot {
        background: radial-gradient(circle at bottom left, rgba(50, 90, 158, .4), transparent 20%), radial-gradient(circle at top right, rgba(21, 168, 112, .2), transparent 40%), radial-gradient(ellipse at top, #0F172A 20%, #1E293B 90%);
    }
</style>
<template>
<div class="bg-spot">
    <div class="bg-green-500">
        <div class="max-w-6xl mx-auto py-4 px-4">
            <h3 class="text-2xl text-green-900 font-bold m-0 p-0">Calculadora de complexidade</h3>
            <h4 class="text-md font-semibold text-green-800">Selecione as características da atividade</h4>
        </div>
    </div>

    <div class="max-w-6xl mx-auto py-4">
        <div class="flex -mx-2">
            <div class="flex items-center px-6 my-2">
                <div class="rounded mr-2 h-14 w-14 bg-green-500 text-green-200 flex items-center justify-center">
                    <span class="font-bold mr-1">{{ totalVisualComplex }}</span> pts
                </div>
                <h4 class="font-semibold text-white">Complexidade visual</h4>
            </div>

            <div class="flex items-center px-6 my-2">
                <div class="rounded mr-2 h-14 w-14 bg-green-500 text-green-200 flex items-center justify-center">
                    <span class="font-bold mr-1">{{ totalComportamentalComplex }}</span> pts
                </div>
                <h4 class="font-semibold text-white">Complexidade comportamental</h4>
            </div>

            <div class="flex items-center px-6 my-2">
                <div class="rounded mr-2 h-14 w-14 bg-green-500 text-green-200 flex items-center justify-center">
                    <span class="font-bold mr-1">{{ totalDatabaseComplex }}</span> pts
                </div>
                <h4 class="font-semibold text-white">Complexidade dos dados</h4>
            </div>
            
            <div class="flex items-center px-6 my-2">
                <div class="rounded mr-2 h-14 w-14 bg-green-500 text-green-200 flex items-center justify-center">
                    <span class="font-bold mr-1">{{ totalTestComplex }}</span> pts
                </div>
                <h4 class="font-semibold text-white">Complexidade dos testes</h4>
            </div>

        </div>
    </div>

    <div class="max-w-6xl mx-auto flex flex-wrap items-start pb-8">
        <div class="w-1/2 px-4">
            <h3 class="m-0 p-0 text-lg font-semibold mb-4 mt-4 text-white">Tarefas visuais</h3>
            <div class="rounded bg-slate-900 p-3 mb-2" v-for="item, index in complexVisualItems" :key="`visual-${index}`">
                <label class="block mb-4 text-green-400 font-semibold">
                    <span class="inline-flex items-center justify-center px-2 py-1 mr-2 text-sm bg-slate-800 font-bold text-green-400 rounded">{{ item.value }} pts</span>
                    Tarefas de {{ item.label }}?
                </label>
                <div class="inline-flex">
                    <button class="h-34 font-bold hover:bg-red-300 hover:text-red-800 text-white text-xl px-2 w-10 bg-red-500 rounded-l"  @click="decrement(item)">-</button>
                    <div class="text-center w-14 px-2 bg-slate-800 font-semibold text-green-400">
                        {{ item.count }}
                    </div>
                    <button class="h-34 hover:bg-green-300 hover:text-green-800 font-bold text-white text-xl px-2 w-10 bg-green-500 rounded-r" @click="increment(item)">+</button>
                </div>
            </div>
        </div>
        
        <div class="w-1/2 px-4">
            <h3 class="m-0 p-0 text-lg font-semibold mb-4 mt-4 text-white">Tarefas comportamentais</h3>
            <div class="rounded bg-slate-900 p-3 mb-2" v-for="item, index in complexComportamentalItems" :key="`visual-${index}`">
                <label class="block mb-4 text-green-400 font-semibold">
                    <span class="inline-flex items-center justify-center px-2 py-1 mr-2 text-sm bg-slate-800 font-bold text-green-400 rounded">{{ item.value }} pts</span>
                    Tarefas de {{ item.label }}?
                </label>
                <div class="inline-flex">
                    <button class="h-34 font-bold hover:bg-red-300 hover:text-red-800 text-white text-xl px-2 w-10 bg-red-500 rounded-l"  @click="decrement(item)">-</button>
                    <div class="text-center w-14 px-2 bg-slate-800 font-semibold text-green-400">
                        {{ item.count }}
                    </div>
                    <button class="h-34 hover:bg-green-300 hover:text-green-800 font-bold text-white text-xl px-2 w-10 bg-green-500 rounded-r" @click="increment(item)">+</button>
                </div>
            </div>
        </div>

        <div class="w-1/2 px-4">
            <h3 class="m-0 p-0 text-lg font-semibold mb-4 mt-4 text-white">Tarefas Banco de Dados</h3>
            <div class="rounded bg-slate-900 p-3 mb-2" v-for="item, index in complexDatabaseItems" :key="`visual-${index}`">
                <label class="block mb-4 text-green-400 font-semibold">
                    <span class="inline-flex items-center justify-center px-2 py-1 mr-2 text-sm bg-slate-800 font-bold text-green-400 rounded">{{ item.value }} pts</span>
                    Tarefas de {{ item.label }}?
                </label>
                <div class="inline-flex">
                    <button class="h-34 font-bold hover:bg-red-300 hover:text-red-800 text-white text-xl px-2 w-10 bg-red-500 rounded-l"  @click="decrement(item)">-</button>
                    <div class="text-center w-14 px-2 bg-slate-800 font-semibold text-green-400">
                        {{ item.count }}
                    </div>
                    <button class="h-34 hover:bg-green-300 hover:text-green-800 font-bold text-white text-xl px-2 w-10 bg-green-500 rounded-r" @click="increment(item)">+</button>
                </div>
            </div>
        </div>

        <div class="w-1/2 px-4">
            <h3 class="m-0 p-0 text-lg font-semibold mb-4 mt-4 text-white">Tarefas de Testes</h3>
            <div class="rounded bg-slate-900 p-3 mb-2" v-for="item, index in complexTestItems" :key="`visual-${index}`">
                <label class="block mb-4 text-green-400 font-semibold">
                    <span class="inline-flex items-center justify-center px-2 py-1 mr-2 text-sm bg-slate-800 font-bold text-green-400 rounded">{{ item.value }} pts</span>
                    Tarefas de {{ item.label }}?
                </label>
                <div class="inline-flex">
                    <button class="h-34 font-bold hover:bg-red-300 hover:text-red-800 text-white text-xl px-2 w-10 bg-red-500 rounded-l"  @click="decrement(item)">-</button>
                    <div class="text-center w-14 px-2 bg-slate-800 font-semibold text-green-400">
                        {{ item.count }}
                    </div>
                    <button class="h-34 hover:bg-green-300 hover:text-green-800 font-bold text-white text-xl px-2 w-10 bg-green-500 rounded-r" @click="increment(item)">+</button>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script setup>
import { reactive, computed } from 'vue'

const complexVisualItems = reactive([
    {
        label: 'Desenvolvimento visual de baixa complexidade',
        value: 1,
        count: 0
    },
    {
        label: 'Desenvolvimento visual de média complexidade',
        value: 4,
        count: 0
    },
    {
        label: 'Desenvolvimento visual de alta complexidade',
        value: 6,
        count: 0
    },
])

const complexComportamentalItems = reactive([    
    {
        label: 'Desenvolvimento comportamental de complexidade baixa',
        value: 4,
        count: 0
    },
    {
        label: 'Desenvolvimento comportamental de complexidade média',
        value: 6,
        count: 0
    },
    {
        label: 'Desenvolvimento comportamental de complexidade alta',
        value: 8,
        count: 0
    },

])

const complexDatabaseItems = reactive([
    {
        label: 'Desenvolvimento no banco de dados de complexidade baixa',
        value: 4,
        count: 0
    },
    {
        label: 'Desenvolvimento no banco de dados de complexidade média',
        value: 6,
        count: 0
    },
    {
        label: 'Desenvolvimento no banco de dados de complexidade alta',
        value: 8,
        count: 0
    }
])


const complexTestItems = reactive([
    {
        label: 'Cenário de teste simples',
        value: 4,
        count: 0
    },
    {
        label: 'Cenário de teste médio',
        value: 6,
        count: 0
    },
    {
        label: 'Cenário de teste complexo',
        value: 8,
        count: 0
    },
])

const totalVisualComplex = computed(() => complexVisualItems.map(item => item.count * item.value).reduce((val, acc) => val + acc))
const totalComportamentalComplex = computed(() => complexComportamentalItems.map(item => item.count * item.value).reduce((val, acc) => val + acc))
const totalDatabaseComplex = computed(() => complexDatabaseItems.map(item => item.count * item.value).reduce((val, acc) => val + acc))
const totalTestComplex = computed(() => complexTestItems.map(item => item.count * item.value).reduce((val, acc) => val + acc))

const decrement = (item) => {
    if (item.count - 1 < 0) return
    item.count--
}

const increment = (item) => item.count++

</script>