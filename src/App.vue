<script setup>
  import { computed } from 'vue'
  import Card from './components/card.vue';
  import { useDark, useToggle } from "@vueuse/core";
  import dark from './assets/dark_mode.svg';
  import light from './assets/light_mode.svg';

  const isDark = useDark();
  const toggleDark = useToggle(isDark);
  const darkModeImage = computed(() => isDark.value ? dark : light);
  const darkModeButtonColor = computed(() => {
    return {
      'bg-black hover:bg-gray-500': isDark.value,
      'bg-white hover:bg-gray-200': !isDark.value,
      'w-16 h-16 sm:w-20 sm:h-20 md:w-24 md:h-24 fixed bottom-4 right-4 rounded-full flex justify-center items-center z-50': true
    };
  });

  const headerStyle = computed(() => {
    return {
      'text-cyan-100': isDark.value,
      'text-cyan-900': !isDark.value,
      "text-3xl sm:text-4xl md:text-5xl py-2 text-cyan-100 dark:text-cyan-500": true
    };
  });

  const rootDivStyle = computed(() => {
    return {
      'bg-gradient-to-r from-emerald-700 to-indigo-700': isDark.value,
      'bg-gradient-to-r from-emerald-500 to-indigo-200': !isDark.value,
      "min-h-screen w-screen p-4 sm:p-8 md:p-10": true
    };
  });
</script>

<template>
  <div :class="rootDivStyle">
    <header class="flex justify-center mb-6">
      <p :class="headerStyle">
        Pozdrav, ja sam <span class="text-cyan-500">Ime Prezime</span>
      </p>
    </header>
    <hr class="border-1 rounded-4xl border-emerald-100">

    <main>
      <p class="text-2xl text-teal-100/75 py-5 sm:text-xl md:text-2xl">
        Moji omiljeni filmovi: {{ isDark }}
      </p>
      <div class="flex justify-center gap-10 flex-wrap sm:gap-6 md:gap-8">
        <Card />
        <Card />
        <Card />
      </div>

      <button @click="toggleDark()" :class="darkModeButtonColor">
        <img :src="darkModeImage" class="w-8 h-8 sm:w-10 sm:h-10 md:w-12 md:h-12" />
      </button>
    </main>
  </div>
</template>

<style scoped>
  @import "tailwindcss";
</style>
