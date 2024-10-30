<script setup>
import Particule from '@/Components/Particule.vue';
import NavBar from '@/Components/NavBar.vue';
</script>

<template>
    <NavBar />
    <Particule />
    <main class="class">
        <div class="flex flex-row pt-12">
            <div class="w-1/2 flex items-center justify-center text-white">
                <!-- Contenu ici -->
            </div>
            <div class="w-1/2 flex items-center justify-center text-white">
                <div class="max-w-sm rounded-lg shadow-lg overflow-hidden">
                    <img
                        src="images/form.avif"
                        alt="Image description"
                        class="w-full h-48 object-cover img"
                    />
                </div>
            </div>
        </div>
    </main>
</template>

<style>
.class {
    position: relative;
    z-index: 1;
}


@keyframes rotateTilt {
    0% {
        transform: rotateY(0deg) rotateX(0deg);
    }
    25% {
        transform: rotateY(-30deg) rotateX(0deg);
    }
    50% {
        transform: rotateY(0deg) rotateX(0deg);
    }
    75% {
        transform: rotateY(0deg) rotateX(180deg);
    }
    100% {
        transform: rotateY(0deg) rotateX(0deg);
    }
}

.img {
    animation: rotateTilt 6s ease-in-out infinite;
}
</style>
