<template>
    <nav class="style">
        <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4 relative z-10">
            <div class="portfolio text-white text-lg font-bold">
                MyPortfolio
            </div>
            <div class="hidden w-full md:block md:w-auto">
                <ul
                    class="flex flex-col p-4 md:p-0 mt-4 md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0 font-bold">
                    <li class="home">
                        <a :href="route('home')" class="nav-link block py-2 px-3 rounded md:p-0"
                            aria-current="page">Home</a>
                    </li>
                    <li>
                        <a :href="route('identity')" class="nav-link block py-2 px-3 text-white md:p-0">Presentation</a>

                    </li>
                    <li>
                        <a href="#" class="nav-link block py-2 px-3 text-white rounded  md:p-0 ">Experience</a>
                    </li>
                    <li>
                        <a href="#" class="nav-link block py-2 px-3 text-white rounded md:p-0  ">Passion</a>
                    </li>
                    <li>
                        <a href="#" class="nav-link block py-2 px-3 text-white md:p-0 ">Contact</a>
                    </li>
                </ul>
            </div>
        </div>

        <!-- <div class="svg-wrapper">
        <svg class="absolute inset-0 w-full h-full pointer-events-none" viewBox="0 0 200 200">
          <path class="top" d="M5 5 H195" />
          <path class="bottom" d="M5 195 H195" />
          <path class="left" d="M5 5 V195" />
          <path class="right" d="M195 5 V195" />
        </svg>
      </div> -->
    </nav>
</template>

<script setup>
import { onMounted } from 'vue';
import anime from 'animejs/lib/anime.es.js';

onMounted(() => {
    const paths = document.querySelectorAll('path');

    paths.forEach(path => {
        const length = path.getTotalLength();
        path.style.strokeDasharray = length;
        path.style.strokeDashoffset = length; // Commence caché

        anime({
            targets: path,
            strokeDashoffset: [length, 0], // Dessiner le contour
            easing: 'easeInOutQuad',
            duration: 2000, // Durée de l'animation
            loop: true,
            direction: 'alternate',
        });
    });
});
</script>

<style>
@import url('https://fonts.cdnfonts.com/css/noto-sans-vai');

nav {
    /* font-family: 'Noto Sans Vai', sans-serif; */
    position: relative;
    overflow: hidden;
    z-index: 1;
    opacity: 100;
}

.portfolio {
    color: #dfdcff;
    text-shadow:
        1px 1px 0 #f619ef,
        -1px 1px 0 #3b09d4,
        1px -1px 0 #dc19f6,
        -1px -1px 0 #2fa7bc;
}

.style {
    background-image: linear-gradient(0deg, rgb(9, 14, 2), blueviolet);
    /* background-color: black; */
    position: relative;
    border: solid 1px rgb(123, 130, 193);
}

.home {
    color: #19f6e8;
}

.svg-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    /* Pour que les clics passent au-dessus du SVG */
}



.nav-link:hover {
    color: #19f6e8;
    transform: rotateZ(360deg);

}
</style>
