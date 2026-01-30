<script setup lang="ts">
import CatIcon from './icons/catIcon.vue';

defineEmits(['fecharDialog'])
</script>

<template>
  <div class="bg-black/60 inset-0 absolute z-1 backdrop-blur-[2px]">
  </div>
  <section class="absolute bottom-0 left-0 z-3 bg-white h-7/9 w-full rounded-t-3xl">
    <button class="absolute right-0 p-md text-primary" @click="$emit('fecharDialog')">
      <i class="material-symbols-outlined" style="font-size: 30px;">
        close
      </i>
    </button>
    <header class="p-md flex items-center gap-4 shadow-[0px_1px_3px_rgba(0,0,0,0.1)]">
      <div class="bg-primary/25 rounded-2xl w-17 p-2">
        <CatIcon class="fill-primary" />
      </div>
      <div>
        <h2 class="text-2xl font-bold">Coleção</h2>
        <div>1 de 2 gatos</div>
      </div>
    </header>
    <section class="relative h-full">
      <ul class="flex flex-wrap justify-center gap-7 absolute inset-0 overflow-y-auto py-10 mb-35">
        <li class="card bg-black w-35 h-45 rounded-2xl"></li>
        <li class="card bg-black w-35 h-45 rounded-2xl"></li>
        <li class="card bg-black w-35 h-45 rounded-2xl"></li>
        <li class="card bg-black w-35 h-45 rounded-2xl"></li>
        <li class="card bg-black w-35 h-45 rounded-2xl"></li>
        <li class="card bg-black w-35 h-45 rounded-2xl"></li>
        <li class="card bg-black w-35 h-45 rounded-2xl"></li>
        <li class="card bg-black w-35 h-45 rounded-2xl"></li>
      </ul>
    </section>
  </section>
</template>
