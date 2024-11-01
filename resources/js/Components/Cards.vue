
<template>
    <div class="cards-container">

        <div class="card max-w-sm rounded-lg shadow" @mouseenter="animateCardText" @mouseleave="resetAnimation">
            <div class="p-5 rounded-lg">
                <a :href="route ('identity')">
                    <h5 class="header mb-2 text-2xl font-bold tracking-tight">Présentation</h5>
                    <div class="mb-3 font-normal title">Here are the biggest enterprise technology acquisitions of 2021 so
                        far, in reverse chronological order...</div>

                </a>
            </div>
        </div>
        <div class="card max-w-sm rounded-lg shadow" @mouseenter="animateCardText" @mouseleave="resetAnimation">
            <div class="p-5 rounded-lg">
                <a href="#">
                    <h5 class="header mb-2 text-2xl font-bold tracking-tight">Experience</h5>
                </a>
                <div class="title">SplitText makes it easy to break apart the text in an HTML element so that each
                    character, word, and/or line is wrapped in its own div tag.</div>
                <a href="#" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white">
                    GO
                    <svg class="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                        fill="none" viewBox="0 0 14 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M1 5h12m0 0L9 1m4 4L9 9" />
                    </svg>
                </a>
            </div>
        </div>
        <div class="card max-w-sm rounded-lg shadow" @mouseenter="animateCardText" @mouseleave="resetAnimation">
            <div class="p-5 rounded-lg">
                <a href="#">
                    <h5 class="header mb-2 text-2xl font-bold tracking-tight">Passions</h5>
                </a>
                <div class="mb-3 font-normal title">Here are the biggest enterprise technology acquisitions of 2021 so
                    far, in reverse chronological order.</div>
                <a href="#" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white">
                    GO
                    <svg class="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                        fill="none" viewBox="0 0 14 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M1 5h12m0 0L9 1m4 4L9 9" />
                    </svg>
                </a>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import anime from 'animejs';

const animationPlayed = ref(false);

const animateCardText = (event) => {
    if (!animationPlayed.value) {
        anime({
            targets: event.currentTarget.querySelectorAll('.title'),
            opacity: [0, 1],
            translateY: [20, 0],
            delay: anime.stagger(200),
            scale: [0.5, 1] ,


            duration: 800,
            easing: 'easeOutQuad',
            complete: () => {
                animationPlayed.value = true;
            },
        });
    }
};

const resetAnimation = () => {
    animationPlayed.value = false;
};

</script>

<style scoped>
@import url('https://fonts.cdnfonts.com/css/noto-sans-vai');
.cards-container {
    display: flex;
    flex-direction: row;
    gap: 16px;
}
.header{
    color: #dfdcff;
    text-shadow:
        1px 1px 0 #f619ef,
        -1px 1px 0 #3b09d4,
        1px -1px 0 #dc19f6,
        -1px -1px 0 #2fa7bc;
}

.card {
    font-family: 'Noto Sans Vai', sans-serif;
    border: 2px solid aqua;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s ease-in-out;
    background-color: black;
    color: white;
}

.card::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 0;
    height: 0;
    background: radial-gradient(circle, blueviolet 0%, transparent 100%);
    transition: width 0.5s ease, height 0.5s ease;
    transform: translate(-50%, -50%);
    border-radius: 50%;
    z-index: 0;
}

.card:hover {
    cursor: pointer;
    transform: translateY(-15px);
    color: thistle;
    border: 2px solid violet;

}

.card:hover h5 {
    color: aqua;
}

.card:hover::before {
    width: 200%;
    height: 200%;
}

.card>.p-5 {
    position: relative;
    z-index: 1;
}
</style>
