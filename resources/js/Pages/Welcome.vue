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

onMounted(() => {
    anime({
        targets: ".line-drawing-demo .lines path",
        strokeDashoffset: [anime.setDashoffset, 0],
        easing: "easeInOutSine",
        duration: 1500,
        delay: (el, i) => i * 250,
        direction: "alternate",
        loop: true,
    });
});
</script>
<template>
    <NavBar />
    <Particule />
    <div class="app-container">
        <div class="content">
            <div class="flex flex-row">
                <div class="relative items-center selection:text-white flex-1">
                    <div class="line-drawing-demo">
                        <svg viewBox="0 0 2000 400">
                            <g fill="none" fill-rule="evenodd" stroke="white" stroke-width="1" class="lines">
                                <g fill="none" fill-rule="evenodd" stroke="white" stroke-width="1" class="lines">
                                    <path class="el"
                                        d="M58 80V50.12C57.7 41.6 51.14 35 43 35a15 15 0 0 0 0 30h7.5v15H43a30 30 0 1 1 0-60c16.42 0 29.5 13.23 30 29.89V80H58z" />
                                    <path class="el" d="M73 80V20H58v60h15z" />
                                    <path class="el"
                                        d="M58 80V49.77C58.5 33.23 71.58 20 88 20a30 30 0 0 1 30 30v30h-15V50a15 15 0 0 0-15-15c-8.14 0-14.7 6.6-15 15.12V80H58zm75 0V20h-15v60h15z" />
                                    <path class="el"
                                        d="M118 80V49.77C118.5 33.23 131.58 20 148 20a30 30 0 0 1 30 30v30h-15V50a15 15 0 0 0-15-15c-8.14 0-14.7 6.6-15 15.12V80h-15zm-7.5-60a7.5 7.5 0 1 1-7.48 8v-1c.25-3.9 3.5-7 7.48-7z" />
                                    <path class="el"
                                        d="M133 65a15 15 0 0 1-15-15v-7.5h-15V50a30 30 0 0 0 30 30V65zm30 15V49.77C163.5 33.23 176.58 20 193 20a30 30 0 0 1 30 30v30h-15V50a15 15 0 0 0-15-15c-8.14 0-14.7 6.6-15 15.12V80h-15z" />
                                    <path class="el"
                                        d="M238 65a15 15 0 0 1 0-30c8.1 0 14.63 6.53 15 15h-15v15h30V49.89C267.5 33.23 254.42 20 238 20a30 30 0 0 0 0 60V65z" />
                                </g>
                            </g>
                        </svg>
                        <Begin />
                    </div>
                </div>
                <div class="flex- w-1/2 text-white">
                    <img src="" alt="Description de l'image" class="width" />
                </div>
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

path {
    fill: transparent;
    stroke: #19f6e8; /* Couleur du contour */
    stroke-width: 3; /* Épaisseur du contour */
  }

  svg {
    width: 100%; /* SVG largeur */
    height: 100%; /* SVG la hauteur */
  }
</style>

<!-- <footer class="py-16 text-center text-sm text-black dark:text-white/70">
    Laravel v{{ laravelVersion }} (PHP v{{ phpVersion }})
    </footer> -->
