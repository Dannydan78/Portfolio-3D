<template>
    <div class="cards-container articles">
        <article class="card" v-for="(item, index) in cards" :key="index" @mouseenter="animateCardText" @mouseleave="resetAnimation">
            <figure>
                <img :src="item.image" alt="Image" />
            </figure>
            <div class="article-body">
                <a :href="item.link">
                    <h2>{{ item.title }}</h2>
                </a>
                <p class="">{{ item.description }}</p>
                <a :href="item.link" class="go inline-flex items-center pt-4">
                    Go
                    <svg class="icon w-3.5 h-3.5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9" />
                    </svg>
                </a>
            </div>
        </article>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import anime from 'animejs';

const animationPlayed = ref(false);

const cards = ref([
    { title: "Présentation", description: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order...", link: route('identity'), image: "images/ordinateur.avif" },
    { title: "Experience", description: "SplitText makes it easy to break apart the text in an HTML element so that each character, word, and/or line is wrapped in its own div tag.", link: "#", image: "images/data.jpeg" },
    { title: "Passions", description: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.", link: "#", image: "images/city.avif" }
]);

const animateCardText = (event) => {
    if (!animationPlayed.value) {
        anime({
            targets: event.currentTarget.querySelectorAll('.title'),
            opacity: [0, 1],
            translateY: [20, 0],
            delay: anime.stagger(200),
            scale: [0.5, 1],
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


article {
    --img-scale: 1.001;
    --title-color: rgb(243, 239, 239);
    --link-icon-translate: -20px;
    --link-icon-opacity: 0;
    position: relative;
    border-radius: 16px;
    box-shadow: none;
    background: rgba(79, 80, 80, 0.4);
    transform-origin: center;
    transition: all 0.4s ease-in-out;
    overflow: hidden;
    color: azure;
}

article a::after {
    position: absolute;
    inset-block: 0;
    inset-inline: 0;
    cursor: pointer;
    content: "";
}

article h2 {
    margin: 0 0 18px 0;
    font-size: 1.9rem;
    color: var(--title-color);
    transition: color 0.3s ease-out;
}

figure {
    margin: 0;
    padding: 0;
    aspect-ratio: 16 / 9;
    overflow: hidden;
}

article img {
    max-width: 100%;
    transform-origin: center;
    transform: scale(var(--img-scale));
    transition: transform 0.4s ease-in-out;
}

.article-body {
    padding: 24px;
}

article a {
    display: inline-flex;
    align-items: center;
    text-decoration: none;
    color: #28666e;
}

article a:focus {
    outline: 1px dotted #28666e;
}

article a .icon {
    min-width: 24px;
    width: 24px;
    height: 24px;
    margin-left: 5px;
    transform: translateX(var(--link-icon-translate));
    opacity: var(--link-icon-opacity);
    transition: all 0.3s;
}

article:has(:hover, :focus) {
    --img-scale: 1.1;
    --title-color: #19f6e8;
    --link-icon-translate: 0;
    --link-icon-opacity: 1;
    background: rgba(138, 43, 226, 0.5);
    cursor: pointer;
    transform: translateY(-15px);
    /* border: 2px solid rgba(246, 25, 239, 0.5); */
    /* box-shadow: rgba(0, 0, 0, 0.16) 0px 10px 36px 0px, rgba(0, 0, 0, 0.06) 0px 0px 0px 1px; */
}

.cards-container {
    display: grid;
    max-width: 1200px;
    margin-inline: auto;
    padding-inline: 24px;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 24px;

}

.go{
    color: #19f6e8;
}
</style>
