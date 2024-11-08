<template>
    <nav class="style">
        <div class="max-w-screen-xl flex flex-wrap items-center justify-between md:justify-center p-4 relative">
            <div class="hidden w-full sm:w-auto md:block md:w-auto">
                <ul class="flex flex-col p-4 md:p-0 mt-4 md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0 font-bold space-x-12">
                    <li class="home">
                        <a :href="route('home')" class="nav-link block py-2 px-3 rounded md:p-0 text-white"
                            aria-current="page">Home</a>
                    </li>
                    <li>
                        <a :href="route('identity')" class="nav-link nav-link-text block py-2 px-3 text-white md:p-0">Présentation</a>
                    </li>
                    <li>
                        <a href="#" class="nav-link block py-2 px-3 text-white rounded md:p-0">Experience</a>
                    </li>
                    <li>
                        <a href="#" class="nav-link block py-2 px-3 text-white rounded md:p-0">Passion</a>
                    </li>
                    <li>
                        <a href="#" class="nav-link block py-2 px-3 text-white md:p-0">Contact</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>


<script setup>
import { onMounted } from 'vue';
import anime from 'animejs/lib/anime.es.js';

const props = defineProps({
    user: {
        type: Object,
    }
});

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

<style scoped>
@import url('https://fonts.cdnfonts.com/css/noto-sans-vai');

nav {
    /* font-family: 'Noto Sans Vai', sans-serif; */
    position: fixed;
    overflow: hidden;
    z-index: 1;
}

ul {
    margin-left: 25rem;
    display: flex;
    gap: 5rem;
    justify-content: center;
}

.portfolio {
    color: #dfdcff;
    /* text-shadow:
        1px 1px 0 #f619ef,
        -1px 1px 0 #3b09d4,
        1px -1px 0 #dc19f6,
        -1px -1px 0 #2fa7bc; */
}

.style {
    background-image: linear-gradient(0deg, rgb(9, 14, 2), rgb(138, 43, 226, 0.8));
    /* background-color: black; */
    position: relative;
    border: solid 1px rgb(123, 130, 193);
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index:100;

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

.nav-link {
    border: solid 1px rgb(138, 43, 226, 0.9);
    padding: 10px 15px;
    border-radius: 25px;
}


.nav-link:hover {

  color: #ffffff;
  background-color: rgb(138, 43, 226, 0.6);
  transition: all 1s ease-out;
}

.nav-link{

}
</style>
