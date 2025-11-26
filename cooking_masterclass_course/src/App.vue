<template>
  <div>
    <HeaderBar :count="wishlist.length" />

    <CourseList 
    :courses="courses"
    :wishlist="wishlist" 
    @toggleWishlist="toggleWishlist"/>
  </div>
</template>

<script setup>
import { ref } from "vue"
import CourseList from "./components/CourseList.vue"
import HeaderBar from "./components/HeaderBar.vue"

const wishlist = ref([])

const courses = ref([
  { 
    id: 1,
    title: "Italian Cuisine Class",
    chef: "Michealangelo Penne",
    price: "R5 000",
    skill: "Beginner",
    available: true,
    img: "https://i.postimg.cc/wTFCZSKq/images-q-tbn-ANd9Gc-Qc-Ad1V0f-VA3791Bi-JL1xl-VFOB5VX4h-XLJn-VQ-s.jpg"
  },
  { 
    id: 2,
    title: "Artistic Sushi Design",
    chef: "Yuta Nakamoto",
    price: "R8 000",
    skill: "Intermediate",
    available: false,
    img: "https://i.postimg.cc/BvT6sXdd/images-q-tbn-ANd9Gc-Qo-XYm-FFQrhb-Wt1oo-Lzvy-Vle-Wv-Bhcr1Om-Q3Ag-s.jpg"
  },
  { 
    id: 3,
    title: "French Pastry Basics",
    chef: "Pierre Je'Taime",
    price: "R6 000",
    skill: "Basics",
    available: true,
    img: "https://i.postimg.cc/pXd8YFR0/images-q-tbn-ANd9Gc-TYb5dx-SEc61hz-LDmm-C6yac-MKVVba-X87VR509Y-Ejpkbpem45t-Zc-Aun-LI-s.jpg"
  },
  { 
    id: 4,
    title: "Dessert Art Design",
    chef: "Anita Love",
    price: "R6 000",
    skill: "Expert",
    available: true,
    img: "https://i.postimg.cc/50bBvKPd/images-q-tbn-ANd9Gc-S7X0k-H-bjr-KN3u-VW-e-Barv-Cdb-Ldyzp-Sj3r-Tw-s.jpg"
  },
  { 
    id: 5,
    title: "Chinese Cuisine Mastery",
    chef: "Huangguang Jun",
    price: "R8 000",
    skill: "Intermediate",
    available: false,
    img: "https://i.postimg.cc/pV89xJk5/images-q-tbn-ANd9Gc-RL13TCD3c-Z98n-URe-Aw-L4PVHczru-VSy1Wsmjw-s.jpg"
  },
  {
    id: 6,
    title: "Thai Dessert Class",
    chef: "Chittaphon Leechaiyapornkul",
    price: "R4 000",
    skill: "Beginner",
    available: true,
    img: "https://i.postimg.cc/GpwwczR1/images-q-tbn-ANd9Gc-Ru2eg3h-L49A2456b-OFhk-Nx-I6wzso-WDFb01zg-s.jpg"
  }
])

function toggleWishlist(course) {
  const index = wishlist.value.findIndex(item => item.id === course.id)
  if (index !== -1) {
    wishlist.value.splice(index, 1) // remove
    console.log(`${course.title} removed`)
  } else {
    wishlist.value.push(course)     // add
    console.log(`${course.title} added`)
  }
}

</script>

<style>
body {
  font-family: Arial, sans-serif;
  background: linear-gradient(
    90deg,
    rgba(194,133,35,1) 0%,
    rgba(76,156,47,1) 50%,
    rgba(237,83,83,1) 100%
  );
  padding: 20px;
}

.wishlist-ping-enter-active {
  animation: pop 0.3s ease-out;
}

@keyframes pop {
  0%   { transform: scale(1); }
  50%  { transform: scale(1.4); }
  100% { transform: scale(1); }
}
</style>