<template>
    <div class="min-w-[1200px] relative">
        <div class="flex justify-between mr-6 ">
            <div class="flex item-cemter font-semibold text-white text2x-l cursor-pointer">
                {{ category }}
            </div>
        </div>

    <!-- </div> -->

    <Carousel
    ref="carousel"
    v-model="currentSlide"
    :item-to-show="8"
    :item-to-scroll="1"
    :wrap-around="true"
    :transition="500"
    snapAlign="start"
    class="bg-transparent"
    
    >
    <Slide
    v-for= "slide, index in movies"
    :key="slide"
    class="flex items-center object-cover text-white bg-transparent"
    >
    <!-- {{ slide }} -->

    <div
    @click="fullScreenVideo(index)"
    class="object-cover -top-10 w-40 h-50 hover:brightness-125 cursor-pointer"
    :class="
    currentSlide !== index ? 'border-4 border-transparent' : ' border-4 border-white',
    currentSlideObj(slide, index)
    "
    >
    <img 
    style="user-select: none"
    class="pointer-events-none h-100% z-[-1]"
    :src=" '/images/'+slide.name+'.png' " 
    
    > 
</div>


    </Slide>
    <template #addons>
        <Navigation/>

    </template>

</Carousel>
    </div>




</template>




<script setup> 
import{ref, toRefs} from 'vue';
import 'vue3-carousel/dist/carousel.css'
import {Carousel, Slide, Navigation} from 'vue3-carousel'



import { useMovieStore } from '../stores/movie';
import { storeToRefs } from 'pinia';
const useMovie = useMovieStore();
const {movie, showFullVideo } = storeToRefs(useMovie)

let currentSlide = ref(0)

const props = defineProps ({category : String, movies : Array })
const {movies, category} = toRefs(props)

const currentSlideObj = (slide, index) => {
    if(index === currentSlide.value) {
        movie.value = slide
    }
}

const fullScreenVideo = (index)=>{
    currentSlide.value = index
    setTimeout(()=> showFullVideo.value = true, 500)
}

</script>


<style>
.carousel_prev,
.carousel_next,
.carousel_prev:hover,
.carousel_next:hover{
    color: white;
}

</style>