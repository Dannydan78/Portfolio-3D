<script setup>
import Particule from '@/Components/Particule.vue';
import NavBar from '@/Components/NavBar.vue';
import { ref, onMounted } from 'vue';
import dayjs from 'dayjs';


const props = defineProps({
    user: Object,

});

const imageVisible = ref(false);
const nameVisible = ref(false);
const firstNameVisible = ref(false);
const dateVisible = ref(false);
const jobVisible = ref(false);

onMounted(() => {
    setTimeout(() => {
        imageVisible.value = true;
    }, 200);

    setTimeout(() => {
        nameVisible.value = true;
    }, 700);
    setTimeout(() => {
        firstNameVisible.value = true;
    }, 1000);
    setTimeout(() => {
        dateVisible.value = true;
    }, 1300);
    setTimeout(() => {
        jobVisible.value = true;
    }, 1600);
});
</script>

<template>
    <NavBar />
    <Particule />
    <main class="class">
        <div class="flex flex-row pt-12">
            <div class="w-1/2 flex flex-col items-center justify-center text-white">
                <div class="name" :class="{ 'name-visible': nameVisible }">
                    {{ user[0].name }}
                </div>
                <div class="name" :class="{ 'name-visible': firstNameVisible }">
                    {{ user[0].first_name }}
                </div>
                <div class="date pt-4" :class="{ 'date-visible': dateVisible }">
                    {{ dayjs(user[0].date_of_birth).format("DD.MM.YYYY") }}
                </div>
            </div>
            <div class="w-1/2 flex items-center justify-center text-white">
                <div class="max-w-sm rounded-lg shadow-lg overflow-hidden">
                    <img
                        src="images/form.avif"
                        alt="Image description"
                        class="w-full h-48 object-cover img"
                        :class="{ 'img-visible': imageVisible }"
                    />
                </div>
            </div>
        </div>
        <div class="job fixed inset-0 flex flex-col items-center justify-center" :class="{ 'job-visible': jobVisible }">
            {{ user[0].job }}
            <button class="button mt-4">En savoir plus</button>
        </div>

    </main>
</template>


<style>
.class {
    position: relative;
    z-index: 1;
}


.img {
    opacity: 0;
    transform: translateX(100%) scale(1);
    transition: opacity 2s ease, transform 2s ease;
}

.img-visible {
    opacity: 1;
    transform: translateX(0) scale(1);
}


.name {
    font-size: clamp(1rem, 3rem, 5vw);
    color: #dfdcff;
    opacity: 0;
    transform: translateX(-100%);
    transition: opacity 2s ease, transform 2s ease;
    line-height: 1.2;
    text-shadow:
        1px 1px 0 #f619ef,
        -1px 1px 0 #3b09d4,
        1px -1px 0 #dc19f6,
        -1px -1px 0 #2fa7bc;
}

.name-visible {
    opacity: 1;
    transform: translateX(0);
}

.date{
    font-size: clamp(1rem, 2rem, 5vw);
    opacity: 0;
    transform: translateX(-100%);
    transition: opacity 2s ease, transform 2s ease;
}
.date-visible{
    opacity: 1;
    transform: translateX(0) scale(1);

}
.job {
    font-size: clamp(1rem, 3rem, 5vw);
    color: #dfdcff;
    opacity: 0;
    transform: translateY(100%);
    transition: opacity 2s ease, transform 2s ease;
    line-height: 1.2;
    text-shadow:
        1px 1px 0 #f619ef,
        -1px 1px 0 #3b09d4,
        1px -1px 0 #dc19f6,
        -1px -1px 0 #2fa7bc;
}

.job-visible {
    opacity: 1;
    transform: translateX(0) scale(1);
}
.button {
    padding: 10px 20px;
    font-size: 16px;
    font-weight: bold;
    color: rgb(245, 241, 241);
    background-color: #272727;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    box-shadow:
        0 4px 15px rgba(175, 2, 214, 0.2),
        0 0 30px rgba(175, 2, 214, 0.2);
    transition: box-shadow 0.3s ease, transform 0.3s ease;
}

.button:hover {
    box-shadow:
        0 4px 20px rgba(184, 5, 204, 0.3),
        0 0 40px rgba(85, 2, 227, 0.4),
        0 0 60px rgba(10, 130, 191, 0.5);
    transform: scale(1.05);
}



</style>

/*
.button{
padding: 10px 20px;
font-size: 16px;
font-weight: bold;
color: black;
background-color: #f1f1f1;
border: none;
border-radius: 8px;
cursor: pointer;
box-shadow: 0 4px 15px rgba(255, 255, 255, 0.2),
            0 0 30px rgba(255, 255, 255, 0.1); /* Ombre douce autour */
/* transition: box-shadow 0.3s ease, transform 0.3s ease;
}

.button:hover {
box-shadow: 0 4px 20px rgba(255, 255, 255, 0.3),
            0 0 40px rgba(255, 240, 150, 0.4), /* Lumière avec dégradé */
            /* 0 0 60px rgba(255, 200, 100, 0.5);
transform: scale(1.05); /* Légère mise en avant */
/* } */
