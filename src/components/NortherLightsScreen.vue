<script setup lang="ts">
//import hoverEffect from 'hover-effect';

import { ref, onMounted } from 'vue';

const distortion = ref<null | HTMLElement>(null)

onMounted(() => {
   /*  new hoverEffect({
        parent: distortion.value,
        intensity: 0.05,
        image1: './images/north1.jpg',
        image2: './images/north2.jpg',
        displacementImage: './images/heightMap.png'
    }); */
})

</script>

<template>
    <div ref="distortion" class="distortion">
        
    </div>
</template>

<style lang="sass" scoped>
.distortion
    height: 100vh

</style>
