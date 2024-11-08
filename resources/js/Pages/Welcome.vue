<template>
    <NavBar :user="user"/>
    <Particule />
    <div class="app-container box">
        <div class="content">
            <div class="flex flex-col">
                <Begin />
            </div>
            <div class="flex items-center justify-center px-14 mt-20">
                <Cards />
            </div>
        </div>
    </div>
    <PicturesSlide />
    
    <!--<div data-aos="fade-up" data-aos-anchor-placement="bottom-center" class="text-white">zgtzgtbhh</div> -->



</template>

<script setup>
import NavBar from "@/Components/NavBar.vue";
import Cards from "@/Components/Cards.vue";
import Particule from "@/Components/Particule.vue";
import Begin from "@/Components/Begin.vue";
import { onMounted } from "vue";

import AOS from "aos";
import "aos/dist/aos.css";


const props = defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
    user: Object,
});

onMounted(() => {
  // Initialisation d'AOS
  AOS.init({
    duration: 1000, // Durée de l'animation (en millisecondes)
    once: true, // Si `true`, l'animation ne se reproduira pas lors de nouveaux scrolls
  });
});




</script>


<style scoped>
.app-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;

}

.content {
    flex: 1;
    /* background: linear-gradient(140deg, #0f0f49, #bf22b7); */
    z-index: 1;

}

.footer {

}


</style>

<!-- <footer class="py-16 text-center text-sm text-black dark:text-white/70">
    Laravel v{{ laravelVersion }} (PHP v{{ phpVersion }})
    </footer> -->
