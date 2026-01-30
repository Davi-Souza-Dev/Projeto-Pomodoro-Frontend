<script setup lang="ts">
import DialogCardCat from '@/components/dialogCardCat.vue';
import CatIcon from '@/components/icons/catIcon.vue';
import { computed, onMounted, ref } from 'vue';

const isActiveDialogCat = ref(false)
const showElementScreen = ref(true)

const secTotal = ref(30);
const secAtual = ref(0);

const tempoFalta = computed(() => {
  return secTotal.value - secAtual.value
})

const formatTimeTotal = computed(() => {
  const hours = Math.floor(secTotal.value / 3600);
  const minutes = Math.floor((secTotal.value % 3600) / 60);
  const seconds = Math.floor(secTotal.value % 60);

  const h = String(hours).padStart(2, '0');
  const m = String(minutes).padStart(2, '0');
  const s = String(seconds).padStart(2, '0');

  return `${h}:${m}:${s}`;
})

const formatConometro = computed(() => {
  const hours = Math.floor(tempoFalta.value / 3600);
  const minutes = Math.floor((tempoFalta.value % 3600) / 60);
  const seconds = Math.floor(tempoFalta.value % 60);

  const h = String(hours).padStart(2, '0');
  const m = String(minutes).padStart(2, '0');
  const s = String(seconds).padStart(2, '0');

  return `${h}:${m}:${s}`;
})

const percentTime = computed(() => {
  if (showElementScreen.value) return 1;
  return Math.floor((secAtual.value * 100) / secTotal.value)
});

const toogleDialogCat = () => {
  if (isActiveDialogCat.value) {
    isActiveDialogCat.value = false;
    document.body.style.overflow = 'auto'
  }
  else {
    isActiveDialogCat.value = true
    document.body.style.overflow = 'hidden'

  };
}

const toogleCount = () => {
  if (showElementScreen.value) {
    showElementScreen.value = false
  } else {
    showElementScreen.value = true
  }
}

onMounted(() => {
  setInterval(() => {
    secAtual.value=secAtual.value+0.01
  }, 10)
})
</script>

<template>
  <main class="relative p-4 min-h-dvh flex flex-col">
    <DialogCardCat v-if="isActiveDialogCat" @fechar-dialog="toogleDialogCat" />
    <header class="w-full flex justify-between items-center" v-show="showElementScreen">
      <button class="bg-linear-160 from-primary/50 to-primary rounded-md h-12 w-12 flex items-center justify-center">
        <i class="material-symbols-outlined" style="font-size: 35px; color:white;">menu</i>
      </button>
      <button
        class="bg-linear-160 from-primary/50 to-primary text-white rounded-md h-9 w-9 p-1 flex items-center justify-center"
        @click="toogleDialogCat">
        <CatIcon class="fill-white" />
      </button>
    </header>
    <section class=" grow flex flex-col items-center justify-center">
      <h2 class="text-2xl font-bold mb-15" v-show="showElementScreen">O gato descoberto hoje</h2>
      <div class="flex flex-col items-center justify-center gap-6">
        <div class="w-60 h-60 rounded-full" :class="showElementScreen
          ? 'bg-radial-[at_25%_25%] to-primary from-primary/30'
          : 'bg-linear-to-b from-primary/5 from-[calc(90%-var(--percent))] to-primary to-[var(--percent)]'"
          :style="{ '--percent': percentTime + '%' }"></div>
        <span class="text-3xl font-bold">{{ showElementScreen ? formatTimeTotal : formatConometro }}</span>
        <div class="flex items-center gap-3">
          <button
            class="bg-linear-to-b from-primary/50 to-primary w-25 rounded-md shadow-md flex items-center justify-center"
            @click="toogleCount">
            <i class="material-icons" style="font-size: 40px; color:white;" v-if="showElementScreen">play_arrow</i>
            <i class="material-icons" style="font-size: 40px; color:white;" v-else>pause</i>
          </button>
          <button
            class="bg-linear-to-b from-primary/50 to-primary rounded-md shadow-md flex items-center justify-center w-15"
            v-show="showElementScreen">
            <i class="material-symbols-outlined" style="font-size: 35px; color:white;">settings</i>
          </button>
        </div>
      </div>
    </section>
  </main>
</template>
