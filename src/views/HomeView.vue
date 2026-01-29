<script setup lang="ts">
import CatIcon from '@/components/icons/catIcon.vue';

</script>

<template>
  <main class="relative p-4">
    <header class="w-full flex justify-between items-center">
      <button class="bg-linear-160 from-primary/50 to-primary rounded-md h-12 w-12 flex items-center justify-center">
        <i class="material-symbols-outlined" style="font-size: 35px; color:white;">menu</i>
      </button>
      <button class="bg-linear-160 from-primary/50 to-primary text-white rounded-md h-9 w-9 p-1 flex items-center justify-center">
        <CatIcon class="fill-white"/>
      </button>
    </header>
    <section class="mt-20 flex flex-col items-center gap-7">
      <h2 class="text-2xl font-bold">O gato descoberto hoje</h2>
      <div class=" bg-linear-to-b from-primary/5 to-primary w-60 h-60 rounded-full"></div>
      <span class="text-3xl font-bold">50:00</span>
      <div class="flex gap-2">
        <button class="bg-linear-to-b from-primary/50 to-primary w-25 rounded-md shadow-md flex items-center justify-center">
          <i class="material-icons" style="font-size: 40px; color:white;">play_arrow</i>
        </button>
        <button class="bg-linear-to-b from-primary/50 to-primary rounded-md shadow-md flex items-center justify-center w-15">
          <i class="material-symbols-outlined" style="font-size: 35px; color:white;">settings</i>
        </button>
      </div>
    </section>
  </main>
</template>
