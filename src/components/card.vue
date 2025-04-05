<script setup>
  import { computed } from 'vue'
  import { useDark, useToggle } from "@vueuse/core";
  const isDark = useDark();
  const darkModeButtonColor= computed(() => {
    return {
      'bg-black hover:bg-gray-500': isDark.value,
      'bg-white hover:bg-gray-200': !isDark.value,
      'size-15 absolute m-10 w-20 h-20 bottom-0 right-0 rounded-2xl flex justify-center': true
    };
  });
</script>
<template>
    <div class="flex flex-col justify-center items-center">
        <div class="rounded-xl bg-gray-300 flex justify-center items-center h-100 w-60">
            <p class="text-5xl text-gray-500">
                Poster
            </p>
        </div>
        <p class="mt-4 text-xl text-white">
            Naslove filma
        </p>
    </div>
</template>