<template>

<div class="relative h-screen -left-44 w-screen bottom-0 bg-gradient-to-t from-black via-black" >
    <div v-if="!showFullVideo" id="SideNav" class="flex bg-black absolute h-screen left-2">
    <img class="absolute -top-8 w-[35px] mt-20 right-14" src="/images/netflix-logo.png">
    <div>
      <div class="py-2 mx-16 ">
        <div class=" -mx-7 absolute top-40 mt-20">
        <Magnify fillColor="#7A7A7A" :size="40" class="cursor-pointer"/>
      </div>
      </div>
      <div class="mx-10 absolute top-60 mt-16">
        <HomeOutline  fillColor="#7A7A7A" :size="40" class="cursor-pointer"/>
        <div class=" absolute text-red-500 top-6 left-3">___</div>
        <!-- <h2 class="text-red-500 text-lg">______</h2> -->
      </div>
      <div class="mx-3 ml-10 absolute bottom-80 -mb-2">
        <TrendingUp fillColor="#7A7A7A" :size="40" class="cursor-pointer"/>
      </div>
      <div class="mx-10 absolute bottom-60">
        <Television fillColor="#7A7A7A" :size="40" class="cursor-pointer"/>
      </div>
      <div class=" mx-10 absolute bottom-40">
        <MovieOutline fillColor="#7A7A7A" :size="40" class="cursor-pointer"/>
      </div>
      <div class="mx-10 absolute bottom-20">
        <Plus fillColor="#7A7A7A" :size="40" class="cursor-pointer"/>
      </div>


    </div>
    </div>
    <div v-if="!showFullVideo">
      <div class=" flex z-20 top-0 right-0 w-10% h-[50%] bg-black  bg-clip-border">
      <div class=" h-[0px] left-[120px] w-[77%] w-right-0 bg-gradient-to-r from-black via-black">

      <MovieDetails v-if="movie" :movie="movie"/>
      <video
      v-if="movie"
      :src="'/videos/'+movie.name+'.mp4'"
      autoplay
      loop
      class="absolute -top-10 h-[76%] w-100 right-0 "      
      />
    </div>
  </div>
  </div>
    <!-- พระอาทิตอยู่นี่ 42 -->
    
    <div class="absolute z-30 bottom-0 right-0 w-screen h-[55%] pl-[120px] overflow-y-auto">
      <VideoCarousel class="pb-14 pt-14" category="Pupular Movies" :movies="movies[0]"/>
      <VideoCarousel class="pb-14 pt-4 " category="Horror Movies" :movies="movies[1]"/>
      <VideoCarousel class="pb-14 pt-6" category="Featured Movies" :movies="movies[2]"/>
    </div>
  <!-- </div> -->
  <div class="absolute z-20 h-[70%] left-[120px] w-[100%] right-0 bottom-0 bg-gradient-to-t from-black via-black" />
    
    <div v-if="!showFullVideo" class="absolute z-50 p-2 m-4 bg-white bg-opacity-50 rounded-full cursor-pointer">

    <div v-if="showFullVideo">
      <div @click="showFullVideo = false" class="absolute z-50 p-2 m-4 bg-white bg-opacity-50 rounded-full cursor-pointer">
        <ChevronLeft fillColor="FFFFFF" :size="40"/>
      </div>
      <video
      v-if="movie"
      :src="'/videos/'+movie.name+'.mp4'"
      autoplay
      loop
      controls
      class="absolute w-[100vw] h-full object-fit"
      />
    </div>
  </div>

  </div>
 
  </template>
  
  
  <script setup>
  import { onMounted, ref } from 'vue';
  import movies from './stores/movies.json'

  import Magnify from 'vue-material-design-icons/Magnify.vue';
  // import SearchIcon from '@mui/icons-material/Search';
  
  import HomeOutline from "vue-material-design-icons/HomeOutline.vue";
  import TrendingUp from "vue-material-design-icons/TrendingUp.vue";
  import Television from "vue-material-design-icons/Television.vue";
  import MovieOutline from "vue-material-design-icons/MovieOutline.vue";
  import Plus from "vue-material-design-icons/Plus.vue";
  import ChevronLeft from "vue-material-design-icons/ChevronLeft.vue";
  import MovieDetails from '@/components/MovieDetails.vue';

  import VideoCarousel from '@/components/VideoCarousel.vue';
  
  import {useMovieStore} from './stores/movie';
  import {storeToRefs} from 'pinia';
  const useMovie = useMovieStore()
  const {movie, showFullVideo} = storeToRefs(useMovie)


  onMounted(()=>{
    setTimeout(()=> movie.value = movies[0][0], 100)
  })


  
  
  </script>