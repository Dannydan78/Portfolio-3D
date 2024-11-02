<template>
    <div class="flex items-center justify-center mt-8">
      <h1 class="text-white text-4xl font-bold">Welcome to</h1>
      <span class="ml-2 world text-4xl font-bold text-purple-500"> my world</span>
    </div>
    <div class="relative items-center selection:text-white ">
      <canvas ref="canvas" class="webgl"></canvas>
    </div>
    <div class="justify-center">
      <div class="wrapper text-white text-center">
        <h1>GreenSock's TextPlugin<span></span></h1>
        <h2>Set or animate text in sequence. Discover!</h2>
      </div>
    </div>
  </template>

  <script setup>
  import gsap from 'gsap';
  import anime from 'animejs';
  import TextPlugin from 'gsap/TextPlugin';
  import { onMounted, ref, onBeforeUnmount } from 'vue';
  import * as THREE from 'three';

  const canvas = ref(null);
  let scene, camera, renderer, lines = [];

  onMounted(() => {
    // Init GSAP Text Animation
    gsap.registerPlugin(TextPlugin);
    const title = gsap.timeline({ repeat: 1111, repeatDelay: 1, yoyo: true });
    title.to("h1 span", { duration: 4, text: " is so much fun you should try it some time!" });

    // Init Three.js scene
    initThree();
  });

  onBeforeUnmount(() => {
    cleanup();
  });

  function initThree() {
    scene = new THREE.Scene();
    camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    camera.position.z = 5;

    renderer = new THREE.WebGLRenderer({ canvas: canvas.value });
    renderer.setSize(window.innerWidth, window.innerHeight);

    // Points from SVG path coordinates (replace these with actual points)
    const lineData = [
    [[0, 1], [1, 3]],     // First line segment
    [[1, 3], [2, 1]],     // Second line segment
    [[2, 1], [0.5, 2]],   // Third line segment
    [[0.5, 2], [1.5, 2]], // Fourth line segment
    [[1.5, 2], [0, 1]],// Remplacez avec vos propres coordonnées pour chaque segment

    ];

    // Create each line as a Three.js BufferGeometry
    lineData.forEach((points) => {
      const geometry = new THREE.BufferGeometry().setFromPoints(
        points.map(p => new THREE.Vector3(p[0], p[1], 0))
      );
      const material = new THREE.LineBasicMaterial({ color: 0xffffff });
      const line = new THREE.Line(geometry, material);
      line.scale.set(0, 0, 0); // Start with zero scale for reveal animation
      scene.add(line);
      lines.push(line);
    });

    // Animate lines with gsap
    lines.forEach((line, index) => {
      gsap.to(line.scale, {
        x: 1, y: 1, z: 1,
        duration: 1,
        delay: index * 0.2,
        ease: 'power2.inOut'
      });
    });

    animate();
  }

  function animate() {
    requestAnimationFrame(animate);
    renderer.render(scene, camera);
  }

  function cleanup() {
    lines.forEach(line => line.geometry.dispose());
    renderer.dispose();
  }
  </script>

  <style scoped>
  .webgl {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: black;
  }

  .wrapper {
    margin-top: 1rem;
    margin-left: 3rem;
    margin-bottom: 6rem;
    font-size: 3vh;
  }

  h1 span {
    color: #19f6e8;
  }

  path {
    fill: transparent;
    stroke: #19f6e8;
    stroke-width: 3;
  }

  svg {
    width: 100%;
    height: 100%;
  }
  </style>
