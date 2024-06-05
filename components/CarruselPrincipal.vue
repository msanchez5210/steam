<template>
  <UCarousel v-slot="{ item }" :items="items" :ui="{ item: 'basis-full' }" class=" overflow-hidden " arrows>
    <img :src="item" class="w-full" draggable="false">
  </UCarousel>
        
</template>

  
<script setup>
  const items = [
  'carrusel1.svg',
  'carrusel2.svg',
  'carrusel3.jpg'
  ]
 
</script>

<style lang="postcss">
</style>
