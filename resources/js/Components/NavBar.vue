<template>
    <nav class="style">
      <div class="max-w-screen-xl flex flex-wrap mx-auto p-4 justify-end relative z-10">
        <div class="hidden w-full md:block md:w-auto" id="navbar-default">
          <ul class="font-medium flex flex-col p-4 md:p-0 mt-4 md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0 dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700">
            <li class="home">
              <a href="#" class="block py-2 px-3 rounded md:bg-transparent md:p-0 dark:text-white" aria-current="page">Home</a>
            </li>
            <li>
              <a href="#" class="block py-2 px-3 text-white rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent">Presentation</a>
            </li>
            <li>
              <a href="#" class="block py-2 px-3 text-white rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent">Experience</a>
            </li>
            <li>
              <a href="#" class="block py-2 px-3 text-white rounded  md:hover:text-blue-700 md:p-0  ">Passion</a>
            </li>
            <li>
              <a href="#" class="block py-2 px-3 text-white  hover:text-red-500 md:hover:bg-transparent md:border-0 md:p-0 ">Contact</a>
            </li>
          </ul>
        </div>
      </div>

      <div class="svg-wrapper">
        <svg class="absolute inset-0 w-full h-full pointer-events-none" viewBox="0 0 200 200">
          <path class="top" d="M5 5 H195" />
          <path class="bottom" d="M5 195 H195" />
          <path class="left" d="M5 5 V195" />
          <path class="right" d="M195 5 V195" />
        </svg>
      </div>
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
  nav {
    position: relative;
    overflow: hidden;
  }
  .style {
    background-color: rgb(40, 21, 100);
    position: relative;
  }
  .home{
    color: #19f6e8;
  }

  .svg-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none; /* Pour que les clics passent au-dessus du SVG */
  }

  path {
    fill: transparent;
    stroke: #19f6e8; /* Couleur du contour */
    stroke-width: 3; /* Épaisseur du contour */
  }

  svg {
    width: 100%; /* Assurez-vous que le SVG couvre toute la largeur */
    height: 100%; /* Assurez-vous que le SVG couvre toute la hauteur */
  }
  </style>
