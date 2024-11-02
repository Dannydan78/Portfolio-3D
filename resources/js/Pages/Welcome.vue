<template>
    <NavBar />
    <Particule />
    <div class="app-container">
        <div class="content">
            <div class="flex flex-col">
                <Begin />
            </div>
            <div class="flex items-center justify-center px-14">
                <Cards />
            </div>
        </div>
    </div>
    <footer class="footer py-16 text-center text-sm text-black dark:text-white/70">
        Laravel v{{ laravelVersion }} (PHP v{{ phpVersion }})
    </footer>
</template>

<script setup>
import { onMounted } from "vue";
import anime from "animejs/lib/anime.es.js";
import NavBar from "@/Components/NavBar.vue";

import Cards from "@/Components/Cards.vue";
import Particule from "@/Components/Particule.vue";
import Begin from "@/Components/Begin.vue";

defineProps({
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
