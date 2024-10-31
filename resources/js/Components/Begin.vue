<script setup>
import gsap from 'gsap';
import TextPlugin from 'gsap/TextPlugin';
import { onMounted } from 'vue';


gsap.registerPlugin(TextPlugin);

onMounted(() => {

  gsap.defaults({ ease: "none" });

  const title = gsap.timeline({ repeat: 1111, repeatDelay: 1, yoyo: true });
  title.to("h1 span", { duration: 4, text: " is so much fun you should try it some time!" });
});
</script>

<template>
  <div class="wrapper text-white">
    <h1>GreenSock's TextPlugin<span></span></h1>
    <h2>Set or animate text in sequence. Discover!</h2>
  </div>
</template>

<style scoped>
@import url('//fonts.googleapis.com/css2?family=Signika+Negative:wght@300;400&display=swap');

.wrapper {
  margin: 4rem;
  font-family: 'Signika Negative', sans-serif;
  font-size: 2vh;
}

h1 span {
    color: #19f6e8;
}


</style>
