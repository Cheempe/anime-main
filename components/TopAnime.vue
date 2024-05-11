<template>
    <div class="carousel-container">
      <div class="carousel-track" ref="track">
        <div class="carousel-slide" v-for="(item, index) in visibleAnime" :key="index" @click="goAnimePage(item)">
            <img :src="item.images.webp.image_url" :alt="item.title">
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps, toRefs, ref, computed } from 'vue'
  import { useRouter } from 'vue-router'
  
  const props = defineProps({
    topAnime: {
      type: Array,
      required: true
    }
  })
  const { topAnime } = toRefs(props)
  const trackRef = ref(null)
  const cardWidth = 220; 
  
  const visibleAnime = computed(() => {
    if (!topAnime.value || !Array.isArray(topAnime.value)) return []
    return topAnime.value.slice(0, 6)
  })
  
  const router = useRouter()
  const goAnimePage = (anime) => {
    router.push(`/anime/${anime.mal_id}`)
  }
  
  </script>
  
  <style scoped>
  .carousel-container {
    position: relative;
    overflow: hidden;
    width: 100%;
    text-align: center;
  }
  
  .carousel-track {
    gap: 20px;
    display: flex;
    justify-content: space-between;
    overflow-y: auto;

  }
  
  .carousel-slide {
    min-width: 180px;
    max-width: 240px;
    height: 500px;
    border-radius: 10px;
    overflow: hidden;
    cursor: pointer;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease-in-out;
  }

  .carousel-slide img {
    object-fit: cover;
    height: 100%;
    border-radius: 10px;
    -webkit-transition: 0.15s all;
  }
  
  .carousel-slide:hover img  {
    -webkit-filter: brightness(50%);
  }
  
  </style>
  