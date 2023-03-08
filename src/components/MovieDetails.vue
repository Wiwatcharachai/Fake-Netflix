<template>
  <div v-if="movie" class=" absolute z-40 text-white w-[53%] pt-20 left-40">
    <div class=" relative -bottom-8 text-[55px] font-semibold font-serif">{{ movie.name }}</div>
    <div class="flex item-center text-lg pt-4 ">
      <div>{{ movie.year }}</div>
      <div class="relative">
        <span class="absolute left-[2px] -top-[12px] text-[4px]"></span>
        <span class="pl-4">{{ movie.genre.one }}</span>
      </div>

      <div class="relative ">
        <span class="absolute left-[2px] -top-[12px] text-[4px]"></span>
        <span class="pl-4">{{ movie.genre.two }}</span>
      </div>
      <div class="relative">
        <span class="absolute left-[2px] -top-[12px] text-[4px]"></span>
        <span class="pl-4">{{ movie.genre.three }}</span>
      </div>
    </div>
    
    <div class="relative top-4">
        <span class="absolute left-[2px] -top-[12px] text-[4px]"></span>
        <span class="pl-4">{{ movie.description }}</span>
      </div>
  </div>
</template>



<script setup>
defineProps({ movie: Object });
</script>
